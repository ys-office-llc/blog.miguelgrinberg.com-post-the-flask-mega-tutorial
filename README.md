# How to

## How to create a test login user using flask shell

```python
$ flask shell
>>> from werkzeug.security import generate_password_hash
>>> hash = generate_password_hash('test_pass')
>>> from werkzeug.security import check_password_hash
>>> check_password_hash(hash, 'test_pass')
True
>>> u = User(username='test_user', email='test_user@example.org', password_hash=hash)
>>> db.session.add(u)
>>> db.session.commit()
>>> User.query.filter_by(username='test_user')
>>> u = User.query.filter_by(username='test_user').first()
>>> u
<User test_user>
>>> u.check_password('test_pass')
True
```

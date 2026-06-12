---
title: "Wasn't the 'hostname' and 'hostname -f' will result in the same value?need help here"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by alel on 2006-07-20
Hi,

Wasn't the 'hostname' and 'hostname -f' will result in the same value?

I got some problem when the 'hostname' show the value 'mandrak'
while
'hostname -f' show the value 'mandrak.lizret.com'

In the guide of server installation in this URL:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)

Both 'hostname' and 'hostname -f' should show the same result. After reboot for few time, the shown result is still the same.

This is my setting in 'vi /etc/hosts'

127.0.0.1 localhost.localdomain localhost
192.168.0.100 mandrak.lizret.com mandrak

Can anybody please show me how to make both value same

---

### Post by zxee on 2006-07-20
Don't know if this will be helpful but maybe have a look here:
[http://64.233.161.104/search?q=cache:l45pePXq8KEJ:www.icsl.ucla.edu/~shervin/linux/hostname.pdf+hostname+linux&hl=en&gl=us&ct=clnk&cd=24&client=firefox](http://64.233.161.104/search?q=cache:l45pePXq8KEJ:www.icsl.ucla.edu/~shervin/linux/hostname.pdf+hostname+linux&hl=en&gl=us&ct=clnk&cd=24&client=firefox)

---


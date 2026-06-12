---
title: "smb problem"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2009-04-11
I seem to have a problem with smb sharing now. I created an smbuser with the same name as my login, primarily because I got permission problems when using hellanzb and a network computer using a different smb user. The computer wouldn't see the files created by hellanzb until i gave permissions on this user.

So i created a user the same as my login name to fix this problem but I every time i reboot the smb computer the share disappears until I reset the user password again with

smbpasswd username

It's really annoying, does anyone know why it is forgetting the password after reboot?

---

### Post by sonicb00m on 2009-04-13
seems the problem is it doesn't store a different password to the login password. if i use the login password on my networked machine it connects.

---


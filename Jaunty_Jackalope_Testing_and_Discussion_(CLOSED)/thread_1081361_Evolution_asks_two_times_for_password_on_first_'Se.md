---
title: "Evolution asks two times for password on first 'Send/receive messages'"
date: 2009-02-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tiagoscd on 2009-02-26
The Evolution asks for me two times the password (default keyring) for access /usr/bin/evolution when I click the first time on 'Send/Receive Messages' button using Ubuntu Jaunty (alpha4). I try to disable the email accounts and test again, so the software don't asks for it.

Appears who the Evolution asks for 'default keyring' when I try to access the protocol POP.

Sorry for my English and thanks for all!

---

### Post by Wayne_V on 2009-02-26
Are you sure it's not asking for a receiving and sending password?   

Check the "Receiving Email" and "Sending Email" tabs in the Account Editor and see if passwords are required for both and if you have 'Remember password' checked.

---

### Post by tiagoscd on 2009-02-26
I solved the problem deleting the file **~/.gnome2/keyrings/login.keyring** and restarting the system.

Thanks for all!

---


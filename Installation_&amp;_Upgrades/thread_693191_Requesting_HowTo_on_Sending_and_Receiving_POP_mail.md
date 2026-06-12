---
title: "Requesting HowTo on Sending and Receiving POP mail with Mailx"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by TrakerJon on 2008-02-10
[FONT="Arial"]I'm requesting help in setting up my Ubuntu Gutsy desktop so that I can send and receive POP email with an external server using Mailx. Hopefully this isn't terribly complex. I have mailx installed...do I need postfix or is there a simple/easy to configure solution? [/FONT]

---

### Post by Partyboi2 on 2008-02-10
This might help
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

---

### Post by TrakerJon on 2008-02-11
> **Partyboi2 said:**
> This might help
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

Thanks but all I really want to do is be able to send and receive POP3 email using mailx without having to setup an full blown email server...to help others do the same and for the learning experience.

---

### Post by TrakerJon on 2008-02-17
Ok, I've discovered that fetchmail, sendmail, procmail and spamassassin will do the trick. I've managed to configure fetch mail without much effort but sendmail is a little more complex. I have the domain name, smtp/POP3 info I would like to use I just need some guidance on setting up the sendmail.cf file.

---


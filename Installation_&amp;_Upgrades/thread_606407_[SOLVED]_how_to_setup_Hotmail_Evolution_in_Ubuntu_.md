---
title: "[SOLVED] how to setup Hotmail Evolution in Ubuntu 7.10?"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by 7chaos on 2007-11-07
Can anyone help me?
i am new in ubuntu....thx

---

### Post by MrFSL on 2007-11-07
I use Thunderbird with the Webmail plugin:

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by 7chaos on 2007-11-08
> **MrFSL said:**
> I use Thunderbird with the Webmail plugin:

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

Thx! I am not only new in Ubuntu, but also new in computer...anyway, i am trying to understand these things. Ubuntu is cool!:guitar:

---

### Post by MrFSL on 2007-11-08
Alrighty, well since your new I will clarify a bit. Thunderbird is a different email client made by Mozilla (the people that bring you firefox web browser.) It can be installed by:

```
sudo apt-get install mozilla-thunderbird
```

Once installed you can install add-ons that extend the functionality of the email client. Webmail is one such add on.

---

### Post by 7chaos on 2007-11-09
> **MrFSL said:**
> Alrighty, well since your new I will clarify a bit. Thunderbird is a different email client made by Mozilla (the people that bring you firefox web browser.) It can be installed by:

```
sudo apt-get install mozilla-thunderbird
```

Once installed you can install add-ons that extend the functionality of the email client. Webmail is one such add on.

So it means that Thunderbird and Evolution Mail are similar things, they are both email client? 
i have installed thunderbird using the code, but i do not know how to setup...what is the incoming sever or outgoing sever if i am using Hotmail? 
:confused:

---

### Post by MrFSL on 2007-11-09
Please read instructions found at:

[http://webmail.mozdev.org/setup.html](http://webmail.mozdev.org/setup.html)

---

### Post by 7chaos on 2007-11-09
Thank you!

---

### Post by meho_r on 2007-11-09
Hmmm... Shouldn't here be explained how to setup Hotmail in Evolution? :confused:

---

### Post by ardchoille42 on 2007-11-09
As far as I know, Hotmail does not provide pop3 access, you have to pay extra for that. So, it won't work unless you pay.

Google, however, does provide free pop3 access, I have kimail set up to work with gmail right now.

---

### Post by MrFSL on 2007-11-09
> **ardchoille42 said:**
> As far as I know, Hotmail does not provide pop3 access, you have to pay extra for that. So, it won't work unless you pay.

Google, however, does provide free pop3 access, I have kimail set up to work with gmail right now.

Pop3 access to hotmail is not available through hotmail this is true (not for free anyways). But there are a slew of applications out there that allow you to fake it.

These include the webmail add-on for thunderbird that I mentioned earlier. You point your email client server address to an application which is running on your local machine that is downloading your email, parsing it, and sending it back to you in POP3 standard.

As I said there are a slew of applications that do this. I think that Webmail, from mozilla is he the best and easiest.

If you want to get this working in Evolution I would suggest MrPostman from sourceforge:
[http://mrpostman.sourceforge.net/](http://mrpostman.sourceforge.net/)

---

### Post by unisol on 2007-11-09
go here: [http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

---


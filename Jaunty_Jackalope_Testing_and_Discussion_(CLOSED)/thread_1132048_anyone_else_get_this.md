---
title: "anyone else get this?"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mamamia88 on 2009-04-21
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 620396F19C0042C8
W: You may want to run apt-get update to correct these problems

 when running sudo aptitude update?

---

### Post by go7Ul1ai on 2009-04-21
Did you import the key file of the PPA you wanted to add?

---

### Post by Ratscallion on 2009-04-21
> **mamamia88 said:**
> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 620396F19C0042C8
W: You may want to run apt-get update to correct these problems

 when running sudo aptitude update?

I got this a few times in Intrepid, and would have thought the same will apply to Jaunty.

Try going here and downloading the zip, run that, reboot and check... 
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)

---

### Post by mamamia88 on 2009-04-21
what zip?

---

### Post by taavikko on 2009-04-21
This should work
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9C0042C8
```

---

### Post by mamamia88 on 2009-04-21
ok downloaded ran the script rebooted and i still get the error

---

### Post by Zorael on 2009-04-21
What ppas have you added as software sources? Either in **/etc/apt/sources.list**, or as *.list files in **/etc/apt/sources.list.d/**.

---

### Post by mamamia88 on 2009-04-21
just chrome and moblock

---

### Post by mamamia88 on 2009-04-21
> **taavikko said:**
> This should work
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9C0042C8
```

thank you sir you are my hero

---

### Post by stilling on 2009-04-21
nice

---

### Post by go7Ul1ai on 2009-04-21
Edit: I thought about it, never mind.

---


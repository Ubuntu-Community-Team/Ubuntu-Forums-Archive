---
title: "VirtualBox OSE"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by throese on 2010-11-03
So, I got VirtualBox OSE up and running and Windows XP Pro SP3 works just fine on it. However, as glad as I am that XP runs, I was kinda hoping I could have gotten my Ubuntu 10.04 LTS backup and distros to work. Here's what it says whenever I tried to get either one working.

[http://i54.tinypic.com/2rc8p4g.png](http://i54.tinypic.com/2rc8p4g.png)

So, what can I do to fix it so that I can test my distro so I can give my friend a Linux CD before Monday?

---

### Post by CharlesA on 2010-11-03
Make sure that the ISO is good - verify the md5sum or sha1sum.

---

### Post by NightwishFan on 2010-11-03
I think the isos are not correctly downloaded. Try to check them for errors.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by throese on 2010-11-03
Thank you both, but I used Remastersys Backup to make the .iso files that I'm speaking of. I want to make a successful distribution .iso for my friend so he can have MonoDevelop and everything without having to download anything himself.

---

### Post by wilee-nilee on 2010-11-03
Vbox is working I have Natty running on it with the guest enabled. I would see if the ISO will burn and install in a regular setup.

---

### Post by throese on 2010-11-03
wilee-nilee: What do you mean by regular set up?

---

### Post by wilee-nilee on 2010-11-03
> **throese said:**
> wilee-nilee: What do you mean by regular set up?

It sounded like you are custom making these ISO's, and only testing the install in the virtual. I meant regular install a booted cd installed directly to the HD. I suggested this to confirm the failure, on both platforms.

---

### Post by throese on 2010-11-03
It didn't work while trying to boot from the CDs on the system either. What now?

---

### Post by wilee-nilee on 2010-11-03
> **throese said:**
> It didn't work while trying to boot from the CDs on the system either. What now?

I have never done what your doing so I wish I could be of more help, just didn't want to leave you hanging.

---

### Post by throese on 2010-11-03
I'm trying to figure out this whole ffmpeg and x265 thing as well to make record-MyDesktop work faster at compressing videos. I'll eventually figure out the virtual box stuff.

---

### Post by CharlesA on 2010-11-03
> **throese said:**
> It didn't work while trying to boot from the CDs on the system either. What now?

I don't know.

What I would suggest is rerunning remastersys and then testing the ISO in VBox to see if it'll boot and install.

---

### Post by throese on 2010-11-03
Update: Well, I have both the Ubuntu Desktop and Ubuntu Server .iso files (ORIGINALS) and had downloaded them from [http://www.ubuntu.com/](http://www.ubuntu.com/) and I just tested my server .iso and it let me install it. You see, I have two CDs, one with Desktop and the other with Server (basic systems), the CDs didn't work, but the ISOs do. I have the ISOs saved in multiple places. Both of my external hard drives and my Linux hard drive. Anyway, I just don't understand why remastersys won't work.

Should I try Clonezilla?

---

### Post by CharlesA on 2010-11-03
I don't know if Clonezilla would allow the OS to work on different hardware (but it should, I guess).

Give remastersys another shot and see what happens.

---

### Post by throese on 2010-11-03
I mean to use Clonezilla to back up my system at least, since Remastersys won't give me a properly worked out ISO file. I will NOT give up until I get at least the Distro part to work. I know I'm smart and that with time I can get this figured out. I've been using Linux since July anyway, and recently completely installed it on my system. Only have XP on VBox because none of the other OSes I tried would work (the Ubuntu distribution and backup ISOs and Windows 7)

---


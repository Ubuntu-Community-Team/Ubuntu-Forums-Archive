---
title: "[SOLVED] Installation advice"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by MONODA on 2007-12-17
Hi I have been dual booting ubuntu for about 3 months and have decided that I want to make my computer 100% ubuntu. Right now I have my Ubuntu set up exactly like I want it, I was thinking of just formatting my windows partition and expanding my Ubuntu one but I am not sure which would be better doing that or an entire fresh full system install. Also I would like to know if there is anyway to have ubuntu boot automatically without going into grub but if I press a button(like esc for example) then I could see my boot options. Thank you for your help, I look forward to having a 100% Ubuntu system.

---

### Post by jken146 on 2007-12-17
> **MONODA said:**
> Hi I have been dual booting ubuntu for about 3 months and have decided that I want to make my computer 100% ubuntu. Right now I have my Ubuntu set up exactly like I want it, I was thinking of just formatting my windows partition and expanding my Ubuntu one but I am not sure which would be better doing that or an entire fresh full system install.
The easiest way to do this is to format the windows partition and mount it as a storage place (requires and edit of /etc/fstab).

>  Also I would like to know if there is anyway to have ubuntu boot automatically without going into grub but if I press a button(like esc for example) then I could see my boot options. Thank you for your help, I look forward to having a 100% Ubuntu system.
This is the default if you have no other OS installed.

---

### Post by MONODA on 2007-12-17
Couldnt I just format my windows partition and allocate that free space to my ubuntu partition? Also I have heard that is is a good Idea to have the home directory on a separate partition and have decided that I want to do this but is it possible to do this without reinstalling? thank you.

---

### Post by MONODA on 2007-12-17
I really need some advice any help would be appreciated. Thank you

---

### Post by MONODA on 2007-12-18
I really dont like to bumb my own threads but I could really use some help. Thanks

---

### Post by mukul_d on 2007-12-18
Hi Monoda,

Well, yes you could delete and format the Windows partition and allocate the space to Ubuntu. But what I didn't understand was if you are going to have only one operating system, then why would you care about your installation options?

Just in case, you are looking to retain your capability to boot into Windows, but don't want to be prompted for that option all the time, then the easiest thing you can do is to comment out the line pointing to the Windows boot in /etc/grub.conf.

That way you won't be taken to the Grub screen all the time and you could revert back to Windows should you choose, by just uncommenting the line.

However, if you would like to get rid of Windows off your computer for good, then I would recommend a clean reinstall.

---

### Post by MONODA on 2007-12-18
What I want to do is remove windows completely and have only ubuntu. I will probably do a fresh install. Thank you for your help

---


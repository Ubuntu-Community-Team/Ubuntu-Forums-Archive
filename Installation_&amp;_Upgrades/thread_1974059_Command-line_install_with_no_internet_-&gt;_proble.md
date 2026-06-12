---
title: "Command-line install with no internet -&gt; problem"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by Xtyn on 2012-05-05
I'm trying to install a command line system of Ubuntu 12.04 from an alternate image. I want to install it while not connected to the internet, but it does not let me get past the archive mirror selection. I've tried to skip that step but it won't let me. I've tried manually changing the archive to /cdrom or /media/cdrom.

I've installed Debian netinstall with no internet several times and I've never had this problem.

---

### Post by mips on 2012-05-05
What happens if you disconnect the network cable before booting cd?

If it can't see the network dhcp config will fail and you can choose not to configure the network. Once your install is complete and you have rebooted you can reconfigure your network settings after you plugged the cable back in..

---

### Post by Xtyn on 2012-05-06
> **mips said:**
> What happens if you disconnect the network cable before booting cd?

The DHCP fails and I have some options and I obviously choose not to configure the network at this time but it still gets stuck at the archive mirror. It does not let me get past it.

---

### Post by mips on 2012-05-06
Strange. Did you check the md5sum of your install cd?

Edit: Do you perhaps also have a wireless card installed? If you do you might wanna remove it temporarily.

---

### Post by alezflute on 2012-05-06
So we have to unplug the wireless cards? I'm having trouble also with the regular isos of 12.04 and when I tried the alternate it froze when configuring the network.

---

### Post by mips on 2012-05-06
> **alezflute said:**
> So we have to unplug the wireless cards? 

If it hangs there then it might be worth a try. I'm not saying it will work or it's the best option but something worth trying.

---

### Post by westie457 on 2012-05-06
Do you by any chance have a Broadcom b43xx wireless card installed?

If so, there is a work around for your situation here.

[http://ubuntuforums.org/showpost.php?p=11883375&postcount=6](http://ubuntuforums.org/showpost.php?p=11883375&postcount=6)

Any other wireless card you might be able to adapt this work around however I do not know for definite.

---

### Post by Xtyn on 2012-05-06
> **mips said:**
> Strange. Did you check the md5sum of your install cd?
I only checked the md5sum of the .iso. I actually made a stick and it does give me an error when I try to check its integrity, but I'm pretty sure it's actually fine.

I'm pretty sure this would work with an internet connection, because I did this before.

> **mips said:**
> 
Edit: Do you perhaps also have a wireless card installed? If you do you might wanna remove it temporarily.
I have a wireless card installed, it's an intel 2200 something.

---

### Post by Xtyn on 2012-05-06
> **mips said:**
> If it hangs there
It does not hang in my case, it just gives an error, because it can't connect to the online archive mirror.

---

### Post by Xtyn on 2012-05-06
I've made a CD with that alternate image and it worked with no internet connection.

I don't know why it did not work from that USB stick made with unetbootin. Normal images work fine, alternate images have issues on my stick.

---

### Post by mips on 2012-05-06
> **Xtyn said:**
> Normal images work fine, alternate images have issues on my stick.

I swear by the alternate images, can't remember the last time I downloaded a desktop image.

---


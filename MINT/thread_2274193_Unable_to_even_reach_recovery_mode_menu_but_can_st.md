---
title: "Unable to even reach recovery mode menu but can still access GRUB and Win8.1"
date: 2015-04-18
forum: MINT
---

### Post by h4ck3rc1 on 2015-04-18
Hi,

Apologies if this has been asked elsewhere but most solutions to boot issues I have read thus far rely on recovery mode working.

My issue is:
I am dual booting Linux Mint 17.1 KDE with separate root and home partitions which I can access via Live USB (so data loss is not a concern)
I can access GRUB menu and boot in to Windows 8.1 without a problem, but trying to boot Mint and it just hangs on a black screen.

I tried recovery mode also and it hangs as shown in attached image.
[Link to image]("https://drive.google.com/file/d/0Bx1TenoUn8b4czlVeDg4cDVSZDg/view?usp=sharing")

Any suggestions or advice before I wipe my root partition and re-install Linux? (I just don't want to lose my settings)

EDIT: Image insert did not work so I made link

---

### Post by oldfred on 2015-04-20
Can you boot recovery mode?

Did you export list of installed applications? Or make any manual system wide setting changes that would be in /etc? Grub setting changes? All those should also be backed up. 

I make copies whenever I change something and keep in /home and just backup /home. But if you have server applications like databases or web pages they may have their own folders in / that need backing up. Most user data is in /home and standard desktops primarily use just /home.

---

### Post by h4ck3rc1 on 2015-04-24
> **oldfred said:**
> Can you boot recovery mode?

Did you export list of installed applications? Or make any manual system wide setting changes that would be in /etc? Grub setting changes? All those should also be backed up. 

I make copies whenever I change something and keep in /home and just backup /home. But if you have server applications like databases or web pages they may have their own folders in / that need backing up. Most user data is in /home and standard desktops primarily use just /home.

Hi, thanks for the reply.

No I cannot boot to recovery, when I select that option, it just hangs on a black screen.

No I didn't export a list of applications (not sure how to), not too worried about the data as I mentioned. I can access it via live USB and grab it. Just a hassle.

I have /home on separate partition so I can re-install distro without affecting my stuff.

---

### Post by h4ck3rc1 on 2015-05-11
Any suggestions for how to back up applications?

---


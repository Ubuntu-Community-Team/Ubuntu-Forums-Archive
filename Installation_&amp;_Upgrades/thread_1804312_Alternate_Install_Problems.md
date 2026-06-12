---
title: "Alternate Install Problems"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by hello cruel world on 2011-07-14
I have tried installing ubuntu 11.04 under and encrypted lvm, five times. I used this [guide]("http://ubuntuforums.org/showthread.php?t=1205372"). I completed installation five times, though with errors it seems.

Once booted, I am greeted with the user login and a black background. The mouse still works, but once I sign in I am greeted with the following errors:

1. Could not update ICEauthority file/home/[user]/.ICEauthority

2.There is a problem with config server [...] status 256

3. Nautilus could not create the required folder /home/[username]/.nautilus

I said fudge it, and was going to try installing 10.04 or 10.10 under encrypted lvm and just update it to 11.04 once I get the darn thing to work, but those alternates don't seem to work off of USB. They keep asking for a cdrom driver.

Ideally, I would like to figure out what packages I am missing, if any, and resolve this issue using command prompts. However, if someone can provide some assistance of any kind, I wont turn it down. This is driving me nuts.

If it matters, the computer is a triple-boot set us such:

partition1 - windows7
partition2 -extended
...partition3 - boot
...partition4 - crypto(lvm)
......partiton5 - swapubuntu
......partiton6 - rootubuntu
...partition7 -backtrax
partition8 - storage

No issues with grub loader, though. So I don't think the partitioning is the root of the problem. It has to do with the alternate installer, I am pretty sure. The installer encounters errors during install, with the 11.04 alt_64 version.

---

### Post by steve11911 on 2011-07-14
You might find some help here:

[http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system](http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system)

---

### Post by hello cruel world on 2011-07-15
That didn't help so much. Thanks for giving it a shot, though. I think this [guide]("http://www.coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/") will help with overcoming the nocdrom issue with older alternate installers. I just hope they don't generate the same errors that 11.04 alt did.

---

### Post by steve11911 on 2011-07-15
Thanks for the link.I am loathe to do a fully encrypted install but am filing this just in case.

---

### Post by hello cruel world on 2011-07-15
I'll update the topic, if it works. I am really really hoping it does. =)

---

### Post by hello cruel world on 2011-07-19
Ok, installed through 10.10 alternate 64 though it had to be created on Ubuntu's own start-up disk creator to work without cdrom.

Next, I upgraded to 11.04.

Unity would not display, so I followed a guide for this very issue.

Ubuntu 11.04 alternate x64 iso has errors, so this is the way to properly install 11.04 encrypted alternate.

/PROBLEM SOLVED

---


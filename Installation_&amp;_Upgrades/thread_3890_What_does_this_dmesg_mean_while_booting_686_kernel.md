---
title: "What does this dmesg mean while booting 686 kernel?"
date: 2004-11-10
forum: Installation &amp; Upgrades
---

### Post by Slovak on 2004-11-10
I decided in my efforts toget 3D working to upgrade from the 386kernel to the 686 kernel. I can still boot both. When I boot into the 686 kernel, it loads fine and all seems to run well, but during the boot process, when the dmesg is scrolling by I noticed it says something along these lines...
cannot find ext3 file system /dev/hdb2(maybe just dev hdb2)
mounting tmpfs over /dev

hdb2 is my Ubuntu drive, but is this ok or not that it says this?

---

### Post by ashley_v on 2004-11-10
[QUOTE=][/QUOTE]
 Funny when you boot and see thoose strange messages you wonder what they are so your like....."OMG what was that message to scroll by!"  so you look really fast and you still miss it?

Just wait to the system boots and you can see all that stuff by typing dmesg in a terminal:

dmesg | less

---

### Post by jdong on 2004-11-10
Do you have a reiserfs or XFS formatted drive?

What happens is that Ubuntu's initrd first tries to mount a given partition as ext3, and if it fails then it tries type auto.

It's really harmless.

---

### Post by Slovak on 2004-11-10
reiserfs

---


---
title: "lucid beta 1, luks encrypted disk &amp; plymouth"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by itsagony on 2010-03-30
hi forum,

today i thought i`ll give lucid a try since beta2 is close and major hickups should be gone.

i installed from a kubuntu alternate beta1 iso which worked flawless.

m problem now is the following: i use a whole encrypted hdd (sdb1) to store all private stuff while the system is installed totally unencrypted on sda. the encrypted disk was setup with LUKS ages ago when i used debian. up to karmic i put the following into my /etc/fstab

/dev/mapper/ultima      /media/ultima   auto    defaults        0       0

and the following into my /etc/crypttab

ultima          /dev/sdb1               none    luks,check=ext2,retry=5


in lucid i changed the kernelline to nomodeset to be able to use the nvidia drivers.
after reboot the system goes up to a point in which im asked to mount or skip the encrypted media (S|M).
pressing M brings up a prompt for the passphrase (unfortunately it passes also the lette rM so i had to backspace and enter the passphrase. pressing S also brings up the enter passphrase (so no skipping :)).
after entering the correct passphrase (which annoyingly brings up a new line enter passphrase) after pressing a letter the system is solid dead with something like playmouth (number) was killed. and there my venture into lucid ends. system is solid dead. and as mentioned before the skip option don't work so i cant test what happens if i boot without the encrypted disk.

now my question to the community is:

is this a problem with the old LUKS encryption and can it be solved by using the methos offered by the alternate install or is this a problem with the boot mechanism? and would it be worth to file a bug for this and if yes against which package?

thanks in advance and excuse my poor english ;)

---

### Post by buellman on 2010-04-01
Hi,

I have problems with luks mount at start up, too.
I have 2 encrypted disks (sda and sdb) so my whole System is encrypted (except /boot) and if I try to fire up my system, start up should ask me for passphrase two times: one time for sda (swap and root) and sdb (data). sda alone will be mounted without any problem but sdb has problems. After entering passphrase for sdb I get some sort of dialogue (SM) like you. But I can press S and nothing happens and M doesn't make anything, too.
Yesterday it works a few times by pressing S --> system starts up. But when pressing M I get some sort of root console.
Today start up hangs... S or M... both the same.

Conclusion: there must be some problem :-)

Do you have any idea what to do? Btw.: fstab and cryptsetup are somethinkg different then yours:
fstab: /dev/mapper/backup /mnt/backup ext3 defaults	0 2
crypttab: backup /dev/disk/by-uuid/0acd8573-885b-483b-ae06-1ff4e8121db1 none luks

Greets. Buellman

Ps: have a look  [here]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/532898")
 Looks like our problem.

---

### Post by zenarcher on 2010-04-01
FWIW, I also use full hard drive encryption with Kubuntu and am running Lucid Beta 1 (64 bit) right now.  I use this method for encrypting my hard drive:

[http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html](http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html)

I'm not having any real problems booting up with this hard drive encryption and Lucid Beta 1.  I have none minor issue, however.  When the Kubuntu screen appears, there is no box there asking for passphrase to be entered.  But, I just go ahead and type the passphrase and the stars representing letters typed for the passphrase appear on the screen and when I finish with the passphrase, Beta 1 boots up the rest of the way normally.

The Kubuntu screen looks terrible at this time on my widescreen 21 inch monitor with Nvidia proprietary graphics driver, however it looks fine on my laptop with a regular screen and ATI video.  Likewise, if I use the nvida free default driver, the Kubuntu screen looks fine, as well.  Only a problem after installing the Nvidia proprietary driver.

Don't know if that is any help for you or not, but thought I would offer the information.

Cheers,
zenarcher

---

### Post by buellman on 2010-04-01
Hi zenarcher,

thank you for the link provided. It's the way I install my Ubuntu too and in Lucid it works without a problem as long as I only try to mount my first hdd = sda (boot, encrypted swap, encrypted root). But when trying to automount my second hdd = sdb (encrypted data) at boottime I have to enter the passphrase 2 times because I have to do it for both hdds.
The problem is that if I try to mount that second hdd at boottime I can enter the passphrase for the second hdd but than it sits there and waits and waits and waits and nothing happens.
As I learned from the threadstarter I have to press S (skip) or M (mount) (which is in my opinion not that selfexplaining) to get the bootprocess to finish. I don't see why it is necessary to press S or M after I entered my passphrase the second time.

However. Thanks for the link :-)

Greets. Buellman

---

### Post by itsagony on 2010-04-01
comment out the encrypted disk is fstab works also. you have to mount the disk manually after booting into kde/gnome then.

i hope they get it fixed until lucid release ^^

on  a sidenote: i really dont like the new boot. it cause more trouble then it benefits the normal user ^^.

---


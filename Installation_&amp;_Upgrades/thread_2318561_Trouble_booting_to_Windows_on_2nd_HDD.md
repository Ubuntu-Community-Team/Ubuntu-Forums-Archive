---
title: "Trouble booting to Windows on 2nd HDD"
date: 2016-03-27
forum: Installation &amp; Upgrades
---

### Post by rudwna on 2016-03-27
Hi,

I've just installed Ubuntu on my laptop on a new SSD (/dev/sda) while moving the original HDD (/dev/sdb/, with Windows 10 installed) to optical drive bay using drive caddy.
Ubuntu works fine, but I've been trying to boot into Windows. update-grub found and add new entry for my Windows 10 automatically but failed when try to boot with message:

> 
error: no such device: <serial>
error: hd1 cannot get C/H/S values.
error: hd1 cannot get C/H/S values.

Please any key to continue...


and I still can't find a way to boot to my Windows.
I've suspected that maybe because my Windows was in hibernation from the last use and may cause mounting problem.

Here's my boot-repair log: [http://paste.ubuntu.com/15522048/](http://paste.ubuntu.com/15522048/)

Any advice would greatly be appreciated.
Thanks,

---

### Post by Bucky Ball on 2016-03-27
You may find that the Windows drive must be in the laptop and recognised as sda if Win was installed in the laptop on that drive when you bought it. In fact, many laptops will ONLY boot from sda and you need to do some serious hoop jumping to get sdb to be the boot drive. 

I did something similar to you and put an SSD in a hard drive bay where my optical drive bay used to be, cloned my Ubuntu install to that and then tried to get that to be the boot drive. No way. I spent some hours on it and my workaround is selecting the boot device menu with F12 at boot, choosing the FDD(!) entry, that takes me to a grub list, I then scroll down that to 'sdb' at the bottom and I'm there.

Hopefully someone can chime in with an easier workaround, but the 'boot from sda only' scenario makes things difficult, if that is the case with your machine.

Besides all that, most pain-free seems to be Win owns the first partition, first drive and is installed on the earliest available partition, first drive: sda. Windows doesn't like to be on other drives. You need to coax it. :|

---

### Post by oldfred on 2016-03-27
Grub will not boot a hibernated Windows. Which then also means the fast start up in Windows must be off as that is always on hibernation.

Does system let you directly boot sdb drive from BIOS? We have seen many that do not, but a few that have seemed to work.

If not you just about have to put Windows drive back as sda to be able to directly boot and turn off fast start up. And Windows updates may turn it back on, so have to pay attention.

Then you still may have issues like Bucky Ball discusses depending on how your caddy is configured.

---

### Post by Bucky Ball on 2016-03-27
Yep. I have Windows installed on the original HDD, sda, and Ubuntu, booting by smoke and mirrors, on the caddy, sdb. You were helping me out on my thread about that one I think oldfred, sometime before christmas. 

Never did work out exactly how I got it working in the end, but it works. I could pop out a bootinfo output if it would help ... :)

---

### Post by rudwna on 2016-03-27
Well, I can't boot to sdb directly from BIOS. So I guess I'll have to put my Windows out of hibernation first.
Then see if grub can boot to after that. If that's not worked out then I thought I'll have to do occasional drive swapping.
Just don't wanna try too hard to solve the problem.

Thanks everybody!

---


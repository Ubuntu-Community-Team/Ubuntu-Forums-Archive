---
title: "Unable to boot windows 8 after installing ubuntu 12.10"
date: 2012-12-24
forum: Installation &amp; Upgrades
---

### Post by nobelium102 on 2012-12-24
I have partitioned around 50gb using windows 8.
Then I installed ubuntu using live usb.
Of the 50gb freespace, I used 2gb for "swap" and the rest for ubuntu. 
I have set it as my primary partition. 
After installing, I restarted my computer
Instead of the usual windows 8 start, obviously now I have the purple grub. 
I chose windows 8 (...sd4 or something)
didn't work, it gave me lots of list of errors and told me to press enter to continue which will just bring me back to the original grub menu.

I have installed gparted partition editor.
I have also installed boot repair
Now the purple grub menu has 2 more choices of windows 8 (uefi or something like that)
but all of them won't work
I tried the recommended repairs but there was no luck

Can anybody help?

Have a great holidays guys :P

---

### Post by oldfred on 2012-12-24
Welcome to the forums.

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Grub creates incorrect chain load entries for UEFI Windows. It still creates BIOS type entries, but the new entries with efi in description that Boot-Repair created should work.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Anything that looks like this will not work.
'Windows ...) (on /dev/sdXY)'

---

### Post by nobelium102 on 2012-12-24
> **oldfred said:**
> Welcome to the forums.

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Grub creates incorrect chain load entries for UEFI Windows. It still creates BIOS type entries, but the new entries with efi in description that Boot-Repair created should work.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Anything that looks like this will not work.
'Windows ...) (on /dev/sdXY)'

Here is the link

[http://paste.ubuntu.com/1463189/](http://paste.ubuntu.com/1463189/)

---

### Post by nobelium102 on 2012-12-24
oky....now i am kind of desperate because I need my stuff from win 8
is there a way I can uninstall ubuntu? I just need to go back to how things were

please help](*,)

---

### Post by oldfred on 2012-12-24
Did you try to install EasyBCD? You have a grub4dos which usually comes from EasyBCD?

You somehow created two efi partitions. You will never boot with 2 efi paritions, so the first thing you need to fix is that.

From Ubuntu live install use gparted and remove boot flag from sda4, boot flag can only be on the efi partition which is sda2 in your UEFI system.
You may have seen some old instructions for BIOS/MBR where you have to have a boot flag on the Windows install but those are wrong fro UEFI/gpt installs.

If you remove boot flag from sda4, you may be able to boot both systems.

Boot-Repair has options to change efi files back and then you would have to delete Ubuntu partitions and use Windows to resize back to its original size.

---

### Post by nobelium102 on 2012-12-24
> **oldfred said:**
> Did you try to install EasyBCD? You have a grub4dos which usually comes from EasyBCD?

You somehow created two efi partitions. You will never boot with 2 efi paritions, so the first thing you need to fix is that.

From Ubuntu live install use gparted and remove boot flag from sda4, boot flag can only be on the efi partition which is sda2 in your UEFI system.
You may have seen some old instructions for BIOS/MBR where you have to have a boot flag on the Windows install but those are wrong fro UEFI/gpt installs.

If you remove boot flag from sda4, you may be able to boot both systems.

Boot-Repair has options to change efi files back and then you would have to delete Ubuntu partitions and use Windows to resize back to its original size.

Thanks but that was not the problem. I turn the boot flag on and off in hope of fixing the problem before you mentioned it. I must have left it on
But yeah....that did that fix the problem

It still gives me 5 or 6 errors saying that couldn't use secure boot and stuff...

Any other solutions? I am sorry for being so stupid hahahahahaa I suck at technology

---

### Post by oldfred on 2012-12-24
Have you turned secure boot off in your UEFI menu? Then it should boot.

---

### Post by nobelium102 on 2012-12-24
> **oldfred said:**
> Have you turned secure boot off in your UEFI menu? Then it should boot.
great news is that there is only 2 errors left after turning off secure boot
1st error is "cannot find drivemap"
2nd error says something about the file path to efi something
do you know how to fix these two?

---

### Post by oldfred on 2012-12-24
Are you still booting in UEFI or legacy? It still needs to be UEFI mode, just with secure boot off. Are you sure only boot flag is on efi partition?
Either of above might be the errors as it seems like it cannot find something to boot.

You should be able from UEFI menu select ubuntu as boot device or Windows?

---

### Post by nobelium102 on 2012-12-24
okay ....tooo much technical words

All I know is that I have turned off boot flag from sd4 which is my windows 8 OS
Now only sd2 which is /boot/efi and fat32 has boot flag turned on

I don't know what you mean by UEIF to be honest... 
all I know is that I boot up from my laptop (thinkpad t430 lenovo) and it shows the purple screen ( I am guessing this the grub menu for ubuntu 12.10)
So there is couple of things to choose from like ubuntu and other mode of ubuntu, windows (loader ..sd4) and pretty much it.
I tried windows and it will give me in a purple screen, 2 errors that I have described above.

---

### Post by nobelium102 on 2012-12-24
so in easy words what do i do next?

---

### Post by nobelium102 on 2012-12-24
okay so I checked my BIOS and I now get legacy and UEFI is.
It was on UEFI only mode all the time so I am guessing that couldn't have been the problem.

---

### Post by nobelium102 on 2012-12-24
[http://paste.ubuntu.com/1463673/](http://paste.ubuntu.com/1463673/)

---

### Post by nobelium102 on 2012-12-24
I solved it!!

for future reference.
Turn off secure boot, run boot-repair

---

### Post by oldfred on 2012-12-25
Glad you got it solved. :)

---


---
title: "[SOLVED] (initramfs) when loading live CD"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by want2bdifferent on 2008-11-18
hey all

I have just got an MSI wind U90 and i am unable to load the live CD through my USB flash drive

it boots and all but when i go to the live CD it gets stuck at (initramfs)

any help would be appreciated 

thanks

---

### Post by want2bdifferent on 2008-11-18
bump. i am going to try re-creating the USB, i think that i might be a problem on that, i hope it works, i wanna have ubuntu

---

### Post by want2bdifferent on 2008-11-18
ok i tried to re-do the usb
nothing is working


PLEASE HELP SOMEONE,I really wanna use ubuntu

---

### Post by mren on 2008-11-18
Type 'exit' after (initramfs), then <enter>

---

### Post by want2bdifferent on 2008-11-18
actually it just goes back to (initramfs)

the exact message i am getting is:

BusyBox b1.1.3 (debian 1:1.1.3-5ubuntu12) built-in shell (ash)
Enter 'help' for a list of built in commands

(initramfs)


thanks for the suggestion though

when i type exit and hit enter it just goes back to the same message

---

### Post by want2bdifferent on 2008-11-18
btw extra note i am using ubuntu 8.04

---

### Post by mren on 2008-11-18
> **want2bdifferent said:**
> btw extra note i am using ubuntu 8.04

Then why not give Ubuntu 8.10 a try. Just got upgraded, works much better than 8.04 on my Acer Aspire 5050.

---

### Post by want2bdifferent on 2008-11-18
> **mren said:**
> Then why not give Ubuntu 8.10 a try. Just got upgraded, works much better than 8.04 on my Acer Aspire 5050.
because we have 4 computers on our internet plan, and if we use over 12GB, we get capped, so I am waiting till the end of the download period, or until i get the disk in the mail

---

### Post by want2bdifferent on 2008-11-18
any other suggestions

---

### Post by want2bdifferent on 2008-11-19
bump... any ideas?

---

### Post by want2bdifferent on 2008-11-19
bump...i really want to use ubuntu, so anyother suggestions would be apprieciated

---

### Post by mren on 2008-11-19
> **want2bdifferent said:**
> bump...i really want to use ubuntu, so anyother suggestions would be apprieciated

try acpi=off boot parameter at first boot up screen.

F6, then replace the last -- with acpi=off, then <enter> to boot.

But I don't recommend you to install this version since your BOIS is not fully compatible with 8.04, you can play around if boot up from live-cd successfully.

---

### Post by mren on 2008-11-19
if that doesn't work, try

noapci nolapci

parameters as well

---

### Post by want2bdifferent on 2008-11-19
ok thanks i will try both suggestions and update

---

### Post by want2bdifferent on 2008-11-19
neither have worked, 

I also had an iso of 7.04 laying around and that also did not work, but that was because it did not load the GUI

Also,  when you said that the BIOS is not compatible with 8.04, would it be compatiable with 8.10?

---

### Post by want2bdifferent on 2008-11-19
update:

I have also tried the USB on more then one computer and it only is on this computer it is not working

---

### Post by The_Dark_Lord on 2008-11-19
I had this problem and it turned out to be my old harddrive, try unplugging yours then booting the cd but i got arounf this by choosing the install option when you first boot the cd, it installed and ran alright i just couldnt use the livecd part

---

### Post by want2bdifferent on 2008-11-19
i have tried everything, like mem test install everything nothing works

I do not have a CD drive

i am not willing to pull apart my brand spanking new laptop atm, if i can not get it working i think i will stick with windows or try another distro

---

### Post by want2bdifferent on 2008-11-20
oh ok update, i just realised that it is not bringing up the normal boot menu with all the options on it, rather one in which you have to type what is done

---

### Post by Browser_ice on 2008-11-20
Did you find the solution ?

I have the same problem. Trying to boot from a 8.04 install USB on an IBM ThinkCenter at the office.

I will check the suggested steps in the mean while.

>> added comments

tried all 3 suggested options and no changes. I have the same problem as him.
I cannot and will not make any changes to the PC prior to booting with the USB.

---

### Post by want2bdifferent on 2008-11-22
no i have not.

what did you use to create the disk image on your USB

---

### Post by want2bdifferent on 2008-11-22
I take that back, i ound my 8.04.1 CD layin aroud, copied the files over, downloaded syslinux extracted it on the USB
booted and it worked

---

### Post by want2bdifferent on 2008-11-28
update, i got my 8.10 CD, and it used that by copying syslinux and the CD contents over and all good

---


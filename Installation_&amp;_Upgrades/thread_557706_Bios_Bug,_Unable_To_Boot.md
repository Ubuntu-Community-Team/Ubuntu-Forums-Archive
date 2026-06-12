---
title: "Bios Bug, Unable To Boot"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by pavan_pavan on 2007-09-23
I have tried to install Ubuntu more than 10 times ):P yet I am unsuccessful, Every time i install i have been facing with a problem.

I have a 80gb sata and a 160gb sata, installed windows OS in 160gb and disconnected it as i want to make a clean install of Ubuntu on 80gb i booted using a live cd and then the following error has occurred "busybox1.1 job control turned off..." based on certain posts i modified "other options by pressing F6 i have added the following

ACPI=OFF IRQPOLL.

after that Ubuntu has booted I have installed it but when i restarted this messages pooped up

"NO BOOTABLE MEDIA: INSERT A BOOTABLE DEVICE AND PRESS ENTER"

i inserted live cd and selected "boot from first hard drive" then the boot screen popped
but it is not progressing I am always getting an error message before loading
"[ 61.74318]...MP-BIOS BUG:8254 TIMER NOT CONNECTED TO IO-APIC
LOADING PLEASE WAIT............"
THEN THE BOOT SCREEN APPEARS IN WHICH THE PROGRESS BAR IS NOT PROGRESSING
SOLVE MY PROBLEM  I AM DESPERATE TO DO PROGRAMMING IN LINUX
:p:p:p:

---

### Post by 5-HT on 2007-09-23
Using 'noapic' as a boot option may do the trick  (you can add 'em from the grub menu --at the bottom of the screen it'll let you know how to edit boot options).

---


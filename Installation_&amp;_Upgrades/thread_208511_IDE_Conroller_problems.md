---
title: "IDE Conroller problems?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by halfstep on 2006-07-03
Hi, I'm having problems trying to put Ubuntu on my machine.  Here is my setup:
Asus Motherboard - P5AD2-E
Intel Pentium 4 3.2Ghz
1 ASUS DRW-160BP
1 ASUS DVD-E616P3
4gb ram
2 IDE 280 Gb Hard Drives (I'm planning on installing to the 2nd)

Windows takes up the primary, and the secondary is going to be for Ubuntu.  They are configured in a Raid0 on a IT8212 RaidBios.  I'm wondering if the IDE controller on my mobo isn't supported.  It would seem kind of odd, because its a relatively new mobo.  I remember when I had to install WinXp, I had to use a disc that came with the mobo sothat windows could recognize my IDE so it could use the hard drives.  I'm wondering if I'm experiencing something similar for  Ubuntu.

Here's my problem.  When I try to install it first gives me errors about my cdrom drive:
hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)(this is displayed about 50 times)
irq 185: nobody cared (try booting with the “irqpoll” option
handlers: [<c0252040>](id_intr+0x0/0x200)
[<f891b330>] )usb_hcd_irq+0x0/0x60[usbcore])
Disabling IRQ #185

To fix that, I used the irqpolloption.  Then it would get as far as the detect my hard drives.  It goes to the blank screen and waits a long time.  If I hit ctrl-c it goes to the partitioning menu, but as soon as I choose any option it just goes back to that blank screen.  I think its having trouble detecting/communicating with the drives.  

1)  If I am experiencing this, how can I get logs so someone can better help with my error.

2)  Has anyone else experienced this/have any ideas how to fix it?  Its not a faulty CD, I'm sure of it, I did the md5sum, and have tried a few different discs.  I have also tried the following options:  IDE=nodma

Any Ideas?

Thanks

---

### Post by Ndlovu on 2006-07-18
I had the same problem - I solved it by adding "irqpoll routeirq" to the boot string. See if routeirq doesn't maybe do it for you. I've also heard of others that needed to add noapic as an option also.

---

### Post by nr4g3d on 2006-08-08
My specs: 

MSI Motherboard 865PE Neo2 
3.2ghz Pentium 4 processor 
1 80gb ide harddrive, 1 120gb ide harddrive 
1 sony dvd-rw 

the way I fixed it was changed the settings in the BIOS to go into legacy mode as opposed to native mode. I read in the manual that legacy mode uses the traditional 13-14irqs and native uses them all. 

When I made this switch, it zipped right past these errors and I was able to install dapper :D  

Hope this helps.

---

### Post by BlaineM on 2006-09-18
Man thanks a ton.  I had the same prob, and had no idea about why.  I thought it had to do with the cdrom, because I tried an ata hd to see if it was a sata thing, and the same errors.  but it was that bios setting for the ide.  man what a great day... hahaha.  My new computer breathes Linux.....

---

### Post by tommycai on 2006-09-26
hey how do you change the boot string?

i'm getting what sounds like the same problem it goes to the "adding live cd users" and then it stops right there I left it on for a WHILE and then it went to what loooked like dos.

---


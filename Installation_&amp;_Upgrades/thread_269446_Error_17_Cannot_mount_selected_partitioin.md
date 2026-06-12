---
title: "Error 17: Cannot mount selected partitioin"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by lorenb on 2006-10-01
Just installed the downloaded Kubuntu (dapper Drake) over an older Mandriva install. First time I used the same partitions I had before on sda. When I rebooted from the HDD I got the following:
   GRUB Loading Stage 1.5.
   GRUB loading, please wait
   Error 15
Then it just hangs. Did this with both Ubuntu and Kubuntu. Then I tried a new install but reformatted the entire sda. Ubuntu created only 2 partitions - swap and one giant ext3. Now when I reboot I get the following:
   Booting 'Ubuntu, kernel 2.6.25-26-amd64-generic'
   root (hd2,0)     
   Filesystem type unknown, partition type 0x7
   kernel /boot/vmlinuz-2.6.15-26-amd64-generic  root=/dev/sda1 ro quite splash
   Error 17: Cannot mount selected partition
   Press any key to continue    (goes back to GRUB menu list)

I have and AMD64 3200+ box with 1GB mem, 200GB SATA (sda) with Linux, 200GB SATA (sdb) with Win XP Pro, 200GB ATA mirrored from the Win SATA and a 20GB ATA I use for some backups. Was dual booting with the Mandiva software with no problems.

I don't understand why the message says 'root (hd2,0)' - isn't that one of the ATA drives? 

I tried all three Linux boot options but none worked.

lorenb

---

### Post by Herman on 2006-10-02
Hello, lorenb, try experimenting from Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and find out how to boot your computer. 
Take notes while you are doing it. The same commands that boot your computer from command line grub will work to edit your menu.lst file with as well.
If you cannot get a command line, (by pressing 'c' from a Grub menu), download a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), and burn it to disk and use the Command Line Interface from that.
Regards, Herman :D

---

### Post by andersja on 2006-10-18
This is a known bug; feel free to go to these links and add more information to help the developers fix it:

[https://launchpad.net/distros/ubuntu/+source/grub/+bug/8497]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/8497")
[https://launchpad.net/distros/ubuntu/+bug/66667]("https://launchpad.net/distros/ubuntu/+bug/66667")

---


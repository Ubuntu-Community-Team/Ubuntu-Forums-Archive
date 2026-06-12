---
title: "Ubuntu 12.04/13.04 on HP Pavilion G6 Notebook PC C4M22EA Windows 8 machine."
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by CorneliusC on 2013-07-07
Hi all,
I am new to the forums but, I'm not really new to Ubuntu or other Linux-based systems.
For over a year I've been installing Linux Mint variations and Ubuntu on my old single core Compaq CQ56 laptop that had Windows 7 preinstalled.
My new laptop as in the title bought February/March this year, however, came with Windows 8 preinstalled and after some Googling have learned that not all machines are going to have the exact same methods that I know have prevented Linux distos from being installed or dual booted.
I had tried Ubuntu 12.04.2 and Ubuntu 12.10 on this HP Pavilion G6 and although eventually it had worked, when shutting down and starting up the laptop I would either receive an error at boot and the laptop shut down or an error would appear so fast it couldn't be read and continue to start up.
This laptop is 8GB RAM dual core with 4GB GPU but, running an installed Ubuntu on this was like trying to run Vista on 0.5GB RAM and it felt the system had not been utilizing or had been blocked from using the full power and was running from SWAP.
Also the machine's wireless was not working and the Card Reader didn't seem to exist at all.

This is what I bought: 
[http://www.pcworld.co.uk/gbuk/laptops-netbooks/laptops/refurbished-laptops/hp-pavilion-g6-2244sa-refurbished-15-6-laptop-ruby-red-19572015-pdt.html#longDesc](http://www.pcworld.co.uk/gbuk/laptops-netbooks/laptops/refurbished-laptops/hp-pavilion-g6-2244sa-refurbished-15-6-laptop-ruby-red-19572015-pdt.html#longDesc)

I really don't want to turn my new laptop that's meant to be a better Work Machine for me into an expensive shiny brick and hope someone can help me successfully get rid of Windows 8 and overcome the issues I've had the first time I tried so I can get back to using Linux for my daily and work needs.

Thank you in advance and I apologize if I've posted this in the wrong place!

---

### Post by Sipee on 2013-07-07
Hie HP pavillion G6 use samsung HDD which is the worst change your HDD and try again

---

### Post by CorneliusC on 2013-07-08
the HDD is a 1TB and the only other one I have is a 300GB one from my Compaq CQ56 with a lot of bad sectors on it (it was 500GB when I bought it in 2011), the issue I got when I successfully installed Ubuntu on it was that it seemed it wasn't even using the CPU at all and slower than the live disc.

---

### Post by CorneliusC on 2013-07-09
To update:

I tried again yesterday and, firstly attempted to dual boot with Windows 8 with Ubuntu 13.04 and this went smoothly without a problem after disabling fast boot in Windows 8 then Secure Boot.
Te only issue I had there was that there was no dual boot option and the laptop booted straight to Windows 8 and didn't recognize Ubuntu in the list of OSs.
EasyBCD did not fix the problem for me as I expected and I had tried one or two Command Prompt methods to no prevail, I could boot into Ubuntu if I brought up the boot options but in the end I just checked Ubuntu 13.04 was running well and if all issues found with 12.10/12.04 were fixed and they were, the SD Card, Wireless and Video drivers were all working perfectly and I decided to erase Windows 8 and install Ubuntu 13.04 as the only OS on the machine.
There has been no problem at all since testing from yesterday and, all the programs I use regularly work as expected and Ubuntu 13.04 fully utilizes the power of the machine.

There is one partition /dev/sda1 /boot/efi that remains and Ubuntu 13.04 is installed on /dev/sda2/ so far I will not delete the /boot/efi partition that takes up 97mb in case it causes a problem.

I suppose I can mark this as Solved as I disabled Windows 8 fast boot within Windows' Power Options and with Secure Boot disabled also. Using Ubuntu 13.04 worked on this laptop much better than 12.04/12.10 for me.

---


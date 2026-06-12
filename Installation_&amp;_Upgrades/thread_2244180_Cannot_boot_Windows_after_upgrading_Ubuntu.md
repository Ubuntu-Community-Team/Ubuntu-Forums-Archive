---
title: "Cannot boot Windows after upgrading Ubuntu"
date: 2014-09-14
forum: Installation &amp; Upgrades
---

### Post by sinmpae on 2014-09-14
Here is the scenario of my Lenovo 3000 G430 Laptop:

System configuration:

P4 Dual core T3200 CPU
3GB RAM (1+2 in two slots)
500GB HDD
Partition layout for HDD:
170GB Priamry - NTFS (for Windows installation)
296GB Logical - NTFS (for data drive)
30GB Logical - EXT4 (for Ubuntu /)
4GB Logical - SWAP (for swap area)

I was using above partition layout to run Windows 7 Ultimate and Ubuntu 12.04. At that time there was no problem in the system.

Then I decided to upgrade to Windows 8. I actually fresh installed Windows 8 instead of upgrading. Everything worked properly without any issue (of course I had to restore MBR from Ubuntu live CD by using 'grub-install' and 'update-grub' to make system dual-boot again).

Then I decided to upgrade Ubuntu to 14.04. The upgrade worked without any issue. But in the Ubuntu system I encountered the problem of having high CPU usage very similar with the problem described here.

[http://askubuntu.com/questions/501840/ubuntu-14-04-used-too-much-processor-after-latest-updatest](http://askubuntu.com/questions/501840/ubuntu-14-04-used-too-much-processor-after-latest-updatest)

The problem was almost same as above expect that I did not have any overheat or shutdown problems. I also enabled intel_pstate as described above but not seen any improvement.

I thought it may be due to some wrong user configuration that carried forward from 12.04 to 14.04 so I fresh installed Ubuntu 14.04 by making some changes on partition layout as following:

170GB Primary - NTFS (for Windows installation)
288GB Logical - NTFS (for data drive)
8GB Logical - EXT4 (for Ubuntu /home)
30GB Logical - EXT4 (for Ubuntu /)
4GB Logical - SWAP (for swap area)

But not able to solve the problem.

Then I thought, let's finish Windows 8 installation by installing necessary software first. From that point Windows was not able to boot. I experienced freezing of Windows boot during startup logo, not even able to get into safe mode.

So I decided to reinstall Windows 8, but the system freezed in the same way, even from the boot disk. So, I doubted the on the partition layout which might became unrecognisable to Windows system (it shouldn't ideally but just the sake of confirmation) I unplugged the HDD from my laptop and tried to run Windows 8 installation disk, as boot disks don't require HDD to boot, system should at least go to the installation screen. But the same problem existed even without HDD.

Then I chose Hiren's boot CD which has Mini Windows XP as live edition. It also has the same problem, froze just before the boot logo. (Same bootable disk works well on other PC.)

The Linux based boot disks have no problem to boot. Even my installed Ubuntu 14.04 is working fine except the CPU problem. To confirm the problem is not in CPU itself, I tried to run live disk of Ubuntu 12.04 and it worked perfectly.

Luckily, I had previous backup of Windows 7 so tried to restore it from the installation disk of Windows 7. The booting was very slow but I was able to get the installation screen. From there I restored the backup of Windows 7.

The restore process was extremely slow, took almost 4 hours but completed successfully. Then with hope I booted in Windows 7 but same problem... froze at startup logo.

This entire scenario puzzled me a lot. Why any Windows refuses to boot on my system while Linux distros have no problems to boot.

What I doubt is that Ubuntu 14.04 made some damage in hardware... but is it even possible?

Can someone tell me what exactly happened to my laptop?

---

### Post by oldfred on 2014-09-14
Cannot help much on Windows specific issues.
Windows does run slow if NTFS partition does not have 30% free space. Often housecleaning, defrag and/or chkdsk may help. Beyond the basics you may want to check on the Windows forums.
       [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

Ubuntu should not make any difference to Windows. Windows does not even see Linux partitions and when totally rebooting system does not know another system is installed. There was one case years ago where a modem card remembered settings and either Window or Linux changed settings, but other system did not reset them on startup. So modem card was not configured correctly on reboot. But those type of issues are extremely rare.

Generally you want / (root) smaller like 20GB and /home larger as that is where your data will go. If you only have 8GB for /home it may fill quickly. In your case the one larger partition with /home inside / would be a better configuration. But I keep /home inside / and it only uses about 2GB. But I have all data in my data partitions and am agressive about making sure data even some larger hidden folders like Firefox & Thunderbird profiles are in my shared data partition not /home. I used to share those with XP but do not use XP anymore. But have not reconfigured not to have shared NTFS yet.

What video card do you have? That often makes a lot of performance difference as well.

---

### Post by sinmpae on 2014-09-16
Thanks for your replay.
The laptop uses the integrated graphics from Mobile Intel 4 Series Express Chipset Family.

I totally agree with your reply that Windows and linux should mutually exclusive to each other.
Since, I encountered this problem only after upgrading the ubuntu version so I thought this may be right forum.
I will post the same question in the windows related forums.

---

### Post by sinmpae on 2014-09-18
Finally after several day of testing and guessing of the problem, I managed to solve it. 
The way I solved the problem is astonishingly unknown!

Yesterday I opened my laptop, not whole laptop but just a portion from where one can add/remove HDD/RAM and cleanup the ventilation path (Heat-sink, Cooling fan etc.)
I removed heat-sink and cleaned the aluminium sink where cooling fan blows air, cleaned dust from cooling fan, removed old heat-sink compound from CPU and GPU chip and applied new one then fitted back everything.
That was not the first time I have cleaned it. I usually do it at every 10-12 months interval. I several times opened the whole laptop till last screw, including the screen.

When I powered up my laptop (of course in Ubuntu 14.04), I surprisingly noticed that 'High CPU Usage' gone away. Ubuntu is now running at very low CPU utilization (1% to 4%) in idle condition (while earlier it was around 30% in idle condition). I can even noticed that cooling fan became silent, almost negligible hot air I can feel at the exhaust.
So with excitement I quickly rebooted in Hiren's Boot CD and noticed that 'Mini Windows Xp' has no problem to boot, freezing gone away !!
Then I booted Windows 8 installation disc, as per my hope it also booted correctly and no freezing problem. Then I installed Windows 8 successfully and completed all necessary software installation, restored MBR to bring GRUB bootloader back and now everything is working fine... buttery smooth... !!!

Again, I am puzzled ... !!! I solved the problem somehow but I don't know what exactly the problem was???
Was my CPU overheating due to poor heat dissipation?
Dose Windows have some kind of protection against this CPU heating at boot time that Linux doesn't have?
If it is really the problem of CPU heating then how it solved 'High CPU utilization' problem of my Ubuntu 14.04?

Can someone enlighten me what I am missing here?

---

### Post by oldfred on 2014-09-18
Newer processors do have built in heat sensors, not sure but expect your model also does.

But usually users just complain in the middle of things it just shutsdown. Have not seen high CPU use related to overheating, but then anything is possible?

---


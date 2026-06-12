---
title: "trying to create partition table on wiped hard drive using GParted."
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by dryflyPhan43 on 2012-02-25
I',m new to ubuntu but have used the live cd ( the most recent version and, 9.04 from a text book) and love what I've experienced. I have an ASUS k50j laptop, with an ATA WDC 320 Gib Hard Drive. I was the unknowing recipient of a unlicensed windows 7 installation ( 2 years ago) by a retail service.

The computer sat idle for 2 years and when I tried to update my security software I realized what had happened. So I wiped the hard drive. 

I want to install ubuntu only and I used a commercial application to wipe my hard drive using the DOD 7 pass method.

When trying to use GParted from a live cd, I see I have 280.09 Gib of unallocated space. 255 heads, 63 tracks/sectors, 38913 Cylinders, and  625137345 Total sectors. Path /dev/sda.

When I run fdisk -l in terminal I get nothing, it goes back to a prompt ready for the next command. 
I have spent about 3 hours, of online googling this topic and have nothing but confusion to show for it.

When I run the option of checking my disk from the live cd options-displayed is checking integrity, this may take some time..
then - check finished no errors.

How do I set up a new partiton table for ubuntu only: I can't seem to find a listing via google with that specific set of instructions. I get a message of bad magic number when trying to determine my node size.

Thank you for your time and help. I really look forward to using ubuntu on my Asus, because I'm having trouble with Lion on my Macbook pro.

---

### Post by 23dornot23d on 2012-02-26
If you run the liveCD and do the option install to the full partition what happens ......

As it should use all the available unallocated space and then at the end write the grub and partition information to the drive .......  ready for it to reboot.

[B]Let us know if the installer is not doing this - and any errors that it reports back .
[/B]
But I would think that it should just use all the space available and then write the needed
information to the disc ready for reboot.

---

### Post by ottosykora on 2012-02-26
> **dryflyPhan43 said:**
> with an ATA WDC **320 Gib** Hard Drive. I was the unknowing recipient of a unlicensed windows 7 installation ( 2 years ago) by a retail service.

...

When trying to use GParted from a live cd, I see I have **280.09 **Gib of unallocated space. 255 heads, 63 tracks/sectors, 38913 Cylinders, and  625137345 Total sectors. Path /dev/sda.





.


is it that you are concerned about the numbers being not the same or what exactly?
With gparted otherwise you can set up all partitions you need too. root (/) and home and swap.

---

### Post by coldraven on 2012-02-26
My advice would be to get hold of the 10.04 Live CD. I think its much better than the 9.04 release.
Then just choose "Install" and all should go well.

You could try this if there's a problem:
Boot the live CD
Run Gparted
Delete the existing partition, the space will then shown as "Unallocated"
Then reboot and try to install, Ubuntu should see the entire drive as empty and use it all.

---

### Post by dryflyPhan43 on 2012-02-26
I believe I have a memory issue, after running the "test memory" option from the live CD all I get is a blinking cursor without a response. 

I will make sure the memory card is seated correctly and then retry your recommendations for install with the 10.04 CD. Right now I have the 9.04 and the latest- not sure what the numeric version is, I just had a friend create the ISO last Sunday (02/19/12).

Will post results soon, Thank You for ALL involved with assistance.
I appreciate the directions.

dryflyPhan43

---

### Post by dryflyPhan43 on 2012-02-26
OK 
here is the error message I get when trying to install ubuntu on my hard drive:

"ubi-language failed with exit code 127. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or be broken."

Any suggestions?

dryflyPhan43

---

### Post by gordintoronto on 2012-02-26
What language did you select?

I hope you tried to install the latest version. 10.04 is pretty old, 9.04 even more so.

---

### Post by dryflyPhan43 on 2012-02-27
The version Loaded was the latest. When booting up 11.10 showed up a the very beginning.

English was/is the language used for CD run Ubuntu and for the Install. 

I think I have a memory problem, because running the test leaves me with a blinking cursor no response. 

Does the computer need to be connected to the internet during installation?

---

### Post by gordintoronto on 2012-02-27
Memory might be the issue.

You don't need to be connected to the Internet during installation, in fact that is my preference. If you are connected it spends 10 minutes downloading stuff I don't need.

---

### Post by dryflyPhan43 on 2012-02-28
It worked, I installed 9.10 after correcting the memory issue, and then upgraded to 10.04 successfully.


> My advice would be to get hold of the 10.04 Live CD. I think its much better than the 9.04 release.
Then just choose "Install" and all should go well.

Thank You very much for the directions, as you expressed upon installation the partitions were created. 

My next question - is there a link that recommends safety tweaks to protect my ports and unwanted sharing ori intrusion, via bluetooth or applications I've failed to see ?

I want to be as conservative as possible with firewall, remote connections, or file sharing as possible.

Should I start another thread?

And do I need to upgrade to 11.04?

For some reason, I can not get my ethernet connection to work, even with network tools.

I'm a newbie to ubuntu but not computers in general (hardware or software).

I'll research these issues on my mac via google, before  comprehensive usage of ubuntu.


Grateful to those for taking time to answer seemingly simple questions with care and detail.
dryflyPhan43

---

### Post by gordintoronto on 2012-02-28
Did you replace the memory? Is it possible that your computer is actually a K501J? I strongly suggest more recent versions of Ubuntu than 10.04. You can't upgrade directly to 11.04, you would need to go 10.04 to 10.10. then to 11.04. The chance of a FUBAR installation is very high if you go that route.

Is there a reason you are avoiding recent releases of Ubuntu?

There is no reason for your Ethernet to not work. Can you run Accessories/Terminal and enter the command: lspci
then copy/paste the lines which describe network adapters? (Actually, there is a possible reason: if your OS is older than your computer, some devices might not be supported.)

I've been using Ubuntu for years, and have had no problem with intrusions, viruses, etc. Some of the web sites I visit are dicey at best. I'm behind  a consumer-grade router.

---

### Post by ottosykora on 2012-02-29
> **dryflyPhan43 said:**
> 





My next question - is there a link that recommends safety tweaks to protect my ports and unwanted sharing ori intrusion, via bluetooth or applications I've failed to see ?

I want to be as conservative as possible with firewall, remote connections, or file sharing as possible.


dryflyPhan43



check the sticky threads on the security part of the forum:
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by dryflyPhan43 on 2012-02-29
I did correct my memory issue.

Loaded 9.10 and upgraded without a problem to 10.04. Should I really upgrade to 11.04 if 10.04 is loaded and is running without errors?

Checked out the Security forum and tried to harden firefox with adblocker and Noscript. the only problem is I don't understand how to use Noscript. "Many :Pwebsites liste, that want JS access like twiiter and facebook, without an apparent option to "deny".

I downloaded APPArmor and configured an extremely restrictive profile that I want to remove but don't understand how.

Thank You again for your help, The computer is becoming useful.

dryflyPhan43

---

### Post by dryflyPhan43 on 2012-03-04
gordintoronto was correct, I have experienced some difficulty with my upgrade fron 10.04 to 10.10.

It seems, I started with one set of instructions after updating 10.04 and 1/2 way thru switched to another website. so now I'm getting messages like   can't open"/var/lib/dpkg/lock". then I'm asked to insert the 11.10 disc into the cdrom. It's 99% working (completed?) and I've tried to use the rm command, "the sudo get-apt clean" comand, which seems to work. but I'm still not able to use the computer like 10.04.

There was no power on/off, account icon in the upper toolbar. No wireless indicator,despite being connected, and I had to remove the guest option because I could not control my mouse with the track pad. My wireless logitech dongle is useless now in either my Asus or Mac.

You were correct it's fubared. I want to remove 10.10 and all it's accompanying files and reload 10.10 correctly. I do not have acces to an ISO. Can you suggest a reliable step by step website that will allow me to downgrade or remove, the existing 10.10 files and start over?

Is there a better way? When I boot up, I need to hit f2 so the Boot option shows, choosing the HDD, instead of the OS booting. I can live with tha,t but I'm stuck now.

I did configure my GUFW and saw that there is active listening( maybe my computer) on ports 5353, 53350, and 68. This is where i was having trackpad difficulty, and used a wireless mouse to remove the guest account.

I've downloaded Avast but still need to register. I don't quite get the sequence of events needed to upgrade correctly, and then activate(?).

Any assitance would be appreciated.

dryflyPhan43

---

### Post by oldfred on 2012-03-05
Do you have good backups of your /home or is it a separate partiton. Have you installed a lot of apps and backed up a list of those apps with dpkg?

You can just use manual install and reinstall using the same partitions you have. When you format & reinstall it erases all of your old install.

If you think you want to try to repair install, you may be able to chroot into your system and totally update from inside your broken system.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

After chrooting you can run all the commands on the system to update and clean system.

---

### Post by dryflyPhan43 on 2012-03-06
I tried what drs305 suggested and it did not work.
  
I also followed bodhi-zazen's sugesstions on permissions, after I wiped and re-installed 9.10 and upgraded to 10.04 then 10.10.

I found some interesting thins in "system monitor"- I have activity from 12/09 greyed out in system monitor. That's when I first used Ubuntu, then wiped the HD using a 7 pass zero fill DOD wipe.

In groups I found a groups by the names of "rtkit", nobody, pulse and pulseaudio.
Pulseaudio was usin PAM-tty "to hide 20M of space", with varying frquencys of bandwith, related to 80211. 

I can't get into my BIOS. for some reason the pasword has been changed and it was not me. No one else uses this computer, I'm single and live alone.

But I do know that I had a similar problem with windows. In Ububtu I removed those groups and the activity stopped in system monitor. and I was still able to log on and off, restart, and get on the internet.
One more weird thing- In network connections there was a 4th connection listed along with my wireles and wired, It was named "Master"

The disc I use to install 9.10 is a commercial disc I received with text book. The upgrades were from the internet. Snould I try replacing my wireless driver after wiping the hard drive?

I'm at a loss.

Thank You
dryflyPhan43

p.s. there are 2 files vmlinuz in my system, I'm not sure if they're in root or my Home folder.

---

### Post by oldfred on 2012-03-06
Some things you need to get into BIOS. If you cannot resolve password -  I never set one, then you need to research how to reset. Many systems have a jumper on the motherboard to short or change temporarily to reset. All BIOS settings revert to defaults which often are not optimal. After changing my BIOS to the way I wanted I took snapshots with my camera.

You normally have vmlinuz & vmlinuz.old and the same for kernel as links to the most current kernel & second most current. You can manually boot easier if necessary with the links without having to know exact details of version.

---

### Post by dryflyPhan43 on 2012-03-06
I was able to partion my hard drive so this thread shoudl be marked solved. 

I Have since discovered a slew of other installation issues that involve security and permissions. Perhaps Asus is not well suited for ubuntu. It's a dissapointment given how well it works running straight from the cd, without installation. 

What puzzles me is the erros are all listed in /var/log/btmp, and the note reads- 'this is not a regular file or is not a text file". The greyed out Dates are from 2009 prior to me even purchasing the computer. It's not used and was brand new. the first entry -" 4.2.0 log source=/var/run/rsyslog/ksmg started". If I could jumper the motherboard I would, but I'm not willing to fry the motherboard. 

I will open another thread or use the computer as a tire chock. These "new" issues are never ending and overwhelming. Despite it's purchase date this computer is practically brand new, given the time I've already invested, it isn't worth it. 2 years ago, I shelved the box after purchasing a mac and wanted to get ubuntu up and running so I could sell the box. Since then I've  developed a weird sickness and am unable to work. But not a victim.

I am grateful for the detailed instruction and sound advice. I'll use what I've learned in the future. 

Thank You
dryflyPhan43

---


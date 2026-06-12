---
title: "Lost network devices after 12.10 upgrade on Alienware m11x"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by Garyu on 2013-01-17
I have had 12.10 installed on my Alienware m11x r3 laptop for a while. Works great, after I installed BumbleBee, until today when I did an upgrade.

I was connected on a wireless network. It was several months since I used Ubuntu on the laptop (I've been absent for a while) so I had a lot of updates to apply. I marked the upgrades in Synaptic because I also wanted to install the Evolution communication suite. At first, the downloads were going great downloading at 2 MB per second or faster. Then, it was going slower and slower. Eventually, I was down to 40 kB/s. Then nothing was downloading at all. I thought it was a temporary issue with the network, so I left the computer running, and I didn't have it plugged in so it died from too low battery.

When I turned it on, it checked the harddrive and found an error while mounting /. So I told it to fix the error, and the machine started. However, there were no network devices detected any more. Again, I thought it was a temporary thing, so I rebooted. Again, it checks the harddrive, didn't find an error but rebooted automatically after the check went to 100 %. Next time it started it went straight to login screen, but again I didn't have any network devices detected. Rebooted again, got disk check again, automatic reboot again, and again no network devices detected. 

Now I am on the same laptop, same network, but booted Windows. Works fine. So not a hardware issue. The hard drive is an SSD and has barely been used so whatever issue might be with the hard drive is some sort of file error due to running out of batteries or something such. 

What can I try to remedy this situation?

---

### Post by Garyu on 2013-01-29
After a bit of looking around, it seems there is some sort of firmware problem with intel centrino wireless-N 1000? I do not have internet access, so I cannot post output of lcpci etc. But lspci does tell me that the card is identified as above, however /etc/network/interfaces does not contain anything else than lo (loopback) and if I add eth0 I am only stuck on trying to identify network for a long time at boot and then nothing. Running lshw something command that one page instructed, then I get that both wired and wireless devices are identified somewhere but UNDEFINED or UNUSED or something similar like that.

Thing is... IT WAS WORKING... before I updated... and now it does not work. So... I should have something on my hard drive that can be used to make it work again!

Please, if someone could help me with a solution that does not involve running around with USB sticks from one computer to another and try out things that may or may not work... That would be great. I want to solve this on the computer without having internet access and without using other computers to transfer files, because if there is no way of reverting a failed update then Ubuntu sucks and I prefer not to believe that.

---

### Post by ryanleesipes on 2013-01-29
If you can plug in via an Ethernet cable you can follow these instructions:

[http://askubuntu.com/questions/215397/wifi-not-working-after-updating-12-10](http://askubuntu.com/questions/215397/wifi-not-working-after-updating-12-10)

I had the same problem and following those instructions fixed it.

---

### Post by ryanleesipes on 2013-01-29
Sorry for the double post, but you might also try this command(if you have no internet connection):

sudo modprobe wl

---

### Post by Garyu on 2013-01-30
> **ryanleesipes said:**
> Sorry for the double post, but you might also try this command(if you have no internet connection):

sudo modprobe wl

modprobe says: "FATAL: Module wl not found"

the stuff suggested in the ask ubuntu page (sudo apt-get install linux linux-headers-generic kernel-package) just returns a lot of "Failed to fetch..." and the suggestion to run with "--fix-missing". However, running fix-missing only returns "Internal error, ordering was unable to handle the media swap"...

Thanks for trying though. :)

EDIT: if it was not clear before, both the wire eth0 and the wireless card are deactivated... I only have the loopback in my list of network devices. I am using my computer at work to access the forum.

---

### Post by Garyu on 2013-05-03
I never found a fix for the mentioned situation. Apparently, if the update progress fails, then you are beyond saving.

However, now that 13.04 is out, I have upgraded and the upgrade solved all my problems. So as long as one is willing to wait for the next release of Ubuntu, this type of situation can be fixed.

---


---
title: "Live cd hangs at start up"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by E-Unit on 2012-02-20
I got ubuntu 11.10. I tried installing it a while ago and just again today with the same problem.
I got a new pc build. Sabertooth p67 Intel i7 16GB DDR3 and so on and so forth. I got ubuntu 10.04 to install but it has no driver support for sound OR on board LAN.

So I tried to update to 11.10 but when booting from the live CD all seems well. But when it gets to detecting the USB keyboard and mouse it hangs.

I get a message type thing something like this "usb-0000:001d.0-1.4/input1"
then it just sits there and does nothing.

If there is a post on this issue please direct me to it, otherwise I'm asking for your advise asap. I need to get back to Open source and away from this *ughh* Hate saying it but.... Windows :S.

---

### Post by trimmer on 2012-02-22
Not sure what type of computer you're using. Architecture, speed, memory and all the specs but I had a similar issue. Live CD would boot but installation would have a fatal error and boot the desktop to investigate and repair the issue.

My issue was NOT similar to yours, but I could not overcome the issue with a CD installation.

I followed the instructions at [Ubuntu Community Installation Support]("https://help.ubuntu.com/community/Installation") more specifically, the instructions for [remote installation over SSH]("https://help.ubuntu.com/community/Installation/OverSSH") on that instruction page.

Once those instructions were completed and I rebooted the machine to the newly installed bootstrap all that was let to do was run `apt-get install ubuntu-desktop'. There were a few minor glitches during the installation process with the syncronization of the apt lists and the dpkg status, and if it happens to you you will know. Very specific errors.

If you encounter the same issue I did, I simply ran several commands to resolve the issue:
```
apt-get purge `filename'
apt-get -d install `filename'
apt-get install `filename'
```
I had to go through all three of these commands after trial and error because I found that the purge command would actually not work completely, but it would remove references to the `filename'.postinst and `filename'.postrm scripts that come as part of the .deb. For some reason these files would appear blank and would break the installation process. It happened on random packages, for me it was ubuntu-mono and 3 reverse dependancies that gave me the most trouble. There were about 50 others but like I said, through trial and error the above commands repaired the problems that broke the install process. Once the packages breaking the process were properly installed and apt-get completed without any errors I would simply re-run apt-get install ubuntu-desktop

It sounds complicated, but you also sound like you are looking for the learning process.

Believe it or not, this process was faster than CD install for me. The computer I was installing 10.04 LTS on is slow and has mismatched memory(a bank of ecc and a bank of non-ecc) and a complete CD install would have taken 2 days if it worked. I got this done in a few hours.

Hope this helps. The links to the instructions I provided will work for any distribution including oneiric so long as you modify the commands and sources.list file to match the proper repositories.

---

### Post by E-Unit on 2012-02-26
Thanks for the advice. I went to the Installation Help section (the link you sent) and read up on some of the stuff. Turns out I was led to download and use the alternative .iso installation file as it contained more packages and files needed for the more modern pc builds as opposed to the older pcs which have limited resources/processing capabilities.

It installed fine but when I selected Ubuntu 11.10 from the grub-2 boot menu it gave me a blank screen. I figured out how to toggle different display modes to see what was actually going on and not much did. So I booted into 'Safe' mode and did all my updates and driver installs through that and when I restarted. Selected the Normal boot option for Ubuntu and woala!.

I'm so happy now :):grin:

---


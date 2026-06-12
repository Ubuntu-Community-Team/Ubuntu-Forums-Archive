---
title: "No Audio on Toshiba Laptop"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by stevet73 on 2008-02-18
Thank you in advance. Helping a user that is experiencing no audio on a Toshiba P-105-S6147 using Ubuntu 7.10 with latest updates through 02-18-2008. That model came with Vista, XP has no audio either and Toshiba said per phone support call that no drivers are available foe XP PRO SP2. Any suggestions.

---

### Post by Pumalite on 2008-02-18
Post:
lshw -C sound

---

### Post by stevet73 on 2008-02-18
Thank you

---

### Post by Pumalite on 2008-02-18
Did you get sound? I was just trying to find out if your kernel recognize your card.

---

### Post by stevet73 on 2008-02-18
Still no sound. 
Thanks again.

---

### Post by Pumalite on 2008-02-19
Try installing this:
sudo apt-get install linux-backports-modules-generic
Reboot and run lshw -C sound again and also try 'alsamixer' in the Terminal. Tel me what you get.

---

### Post by CorinneGospel on 2008-02-23
> **Pumalite said:**
> Try installing this:
sudo apt-get install linux-backports-modules-generic
Reboot and run lshw -C sound again and also try 'alsamixer' in the Terminal. Tel me what you get.

Hello there,
I've got the same laptop and I've tried a lot of things and it still doesn't work.
Could you explain how can I configure the sound please? I am a novice in Linux.
Many thanks.

---

### Post by Pumalite on 2008-02-23
Go through the same steps that I posted here and tell me what you get in each of them first.

---

### Post by CorinneGospel on 2008-02-23
Thank you for your reply. I've just tried that and it still doesn't work. I've tried so many things that found on the net as well...

---

### Post by Pumalite on 2008-02-23
Tell me what is the name of your sound card.

---

### Post by CorinneGospel on 2008-02-24
The name of the sound card is Intel HDA included in the Toshiba but when I went to double check on Toshiba website, I saw the sound configuration as:
&#8226; Built-in harman/kardon® stereo speakers
&#8226; Windows Sound System
&#8226; Sound Volume Control Dial
And they give the Windows drivers and call them Conexant audio driver and I've found CX20549 in the Bios configuration. It seems that is a sound card which includes a modem on the Conexant website,

---

### Post by Pumalite on 2008-02-24
lshw -C sound tells you if it's unclaimed. Is it?

---

### Post by CorinneGospel on 2008-02-24
This is what I get


*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by Pumalite on 2008-02-24
It's recognized by your kernel and the module is loaded.
Type in the Terminal:
alsamixer
And tell me what you see.

---

### Post by CorinneGospel on 2008-02-24
What I see is in the attachement. Thanks again for the time spent to help me.

---

### Post by Pumalite on 2008-02-24
Make sure all the volumes are 100%, then try your sound again. Make sure everything is 'on' and not 'off'

---

### Post by CorinneGospel on 2008-02-24
Which entry shall I do because when I'm in Alsamixer, I move the volume up and down but it doesn't change the 00 at the bottom of the volume bar. I'm a novice.

---

### Post by Pumalite on 2008-02-24
The '00' are OK. Read the legend at the top. Move with the arrows.Arrow up increases the volume is you have carried the marker at the bottom with the side arrow.

---

### Post by CorinneGospel on 2008-02-24
This is what I've got now

---

### Post by Pumalite on 2008-02-24
What about the sound?

---

### Post by CorinneGospel on 2008-02-24
Still nothing sorry. Shall I re-install Ubuntu?

---

### Post by Pumalite on 2008-02-24
You could try your hand at compiling the latest alsa-driver:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
If it doesn't work go to [http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage), download the
alsa-driver, lib and utils and follow the Howto at the same address and look for your driver at the Sound card matrix. Then, if needed, apply the patch and add something at the end of /etc/modprobe.d/alsa-base (sudo gedit) at described in the previous link. I do not own the same laptop but I also have got a Intel Sound Card and worked a bit to have a functioning audio.
Another possible solution:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

This worked with a Lenovo 3000:

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot
Code:

sudo gedit /etc/modprobe.d/alsa-base

Add this line at the end of the file:
Code:

options snd-hda-intel model=3stack

Save the file, close it, reboot, and CROSS YOUR FINGERS!

---

### Post by CorinneGospel on 2008-02-24
I will re-install Ubuntu and try that. I get back to you.

---

### Post by Pumalite on 2008-02-24
OK. Good luck.

---

### Post by CorinneGospel on 2008-02-24
Hello there
Before I go any further, I keep receiving this error message when I start.
>  PCI: Cannot allocate resource region 1 of device 0000:00:00.0
Can you help please?
Many thanks.

---

### Post by Pumalite on 2008-02-24
Are you able to get to the Desktop?

---

### Post by CorinneGospel on 2008-02-24
Yes I can reach the Desktop. I realise that the message is more like 
[ 0.668000] PCI: Cannot allocate resource region 7 of device 0000:00:1b.0
[ 0.668000] PCI: Cannot allocate resource region 8 of device 0000:00:1b.0
[ 0.668000] PCI: Cannot allocate resource region 9 of device 0000:00:1b.0
sometimes it says device 1c
but the sound is supposed to be there
I don't really know
Shall I sort that out or shall I install Alsa as advised before?

---

### Post by Pumalite on 2008-02-24
If you are at the Desktop; did you try the sound?

---

### Post by CorinneGospel on 2008-02-24
Yes but unfortunately it still doesn't work. So I will install again the last version of ALSA.
But is it a problem that I keep receiving this PCI problem when I start up?

---

### Post by Pumalite on 2008-02-24
[http://computer.howstuffworks.com/pci.htm](http://computer.howstuffworks.com/pci.htm)

---

### Post by CorinneGospel on 2008-02-24
I don't really understand why you're sending me this link.

---

### Post by Pumalite on 2008-02-24
To ubderstand what PCI is and how it works. Your problem is hardware related and I don't know how to fix it. Sorry.

---

### Post by CorinneGospel on 2008-02-24
Are you sure? Because everything was working fine under Windows.
Don't you have a part of Ubuntu that can modify the configuration?

---

### Post by Pumalite on 2008-02-24
Maybe somebody else knows the answer, but I don't. Sorry.

---

### Post by CorinneGospel on 2008-02-25
Hey there,
I just want to use Ubuntu and nothing else. Do you thing that I could solve the sound problem in installing Ubuntu 8.04 LTS (Hardy Heron) Alpha 5 or any other version?

---

### Post by Pumalite on 2008-02-25
I have Alpha5 and it runs great, but that is not assurance that you will not continue to have problems with Ubuntu. I'd try other distros to find out if you are incompatible with Linux in general or only Ubuntu in particular.

---

### Post by Pumalite on 2008-02-25
You could also give it a try and find out. (if you have a curious, adventurous spirit)

---

### Post by CorinneGospel on 2008-02-26
> **Pumalite said:**
> You could also give it a try and find out. (if you have a curious, adventurous spirit)

Yes, I do have a curious and adventurous spirit! I just like Ubuntu and just wanted it to work correctly. And guess what? I have installed Ubuntu 8.04 LTS (Hardy Heron) Alpha 5 and the sound is working fine. I believe that's the only option to have the sound with the Intel HDA sound card.
I hope others will do the same. :KS

---

### Post by Pumalite on 2008-02-26
Congrats. Good luck.

---


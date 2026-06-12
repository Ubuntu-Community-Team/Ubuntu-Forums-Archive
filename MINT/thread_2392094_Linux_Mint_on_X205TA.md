---
title: "Linux Mint on X205TA"
date: 2018-05-16
forum: MINT
---

### Post by kharshak on 2018-05-16
Hi everyone,

:KS:KS:KS **First of all, many great thanks to harryharryharry and other contributors to succeeding in [hardware support on X205TA]("https://ubuntuforums.org/showthread.php?t=2254322") !!!** :KS:KS:KS

Having finally convinced my wife to use Linux, I tried to install LinuxMint 16.04 (so it's nor so far from Windows) on her X205TA laptop. My searches led me through lots of advices before ending on [this amazing thread]("https://ubuntuforums.org/showthread.php?t=2254322") !
Unfortunately, I had already installed LinuxMint16.04 with the "classic" .iso x64 file and a bootia32.efi on a USB Stick before I found the [harryharryharry's isos]("http://x205ta.myftp.org:1337/isos/")...
[LIST]
[*]What works :
[LIST]
[*]Wifi 
[*]Sound by speakers 
[/LIST]
  
[*]What does not work :
[LIST]
[*]Sound by headphones or LineOut 
[*]Hibernation (I read on a recent post that it's never working) 
[*]Freezing (often when using Firefox) 
[/LIST]
  
[*]What is not tested :
[LIST]
[*]Bluetooth 
[/LIST]
  
[*]What I have done for that :
[LIST]
[*]Installing LinuxMint 16.04 x64 
[*]Copying nvram* to .../brcm/brcmfmac43340-sdio.txt ... (Wifi) 
[*]Upgrade from kernel 4.10.0-38 to kernel 4.13.0-41 
[*]##### Audio (like in previous TheNightHawk's post)

sudo mkdir -p /usr/share/alsa/ucm/chtrt5645
sudo rm -rf /usr/share/alsa/ucm/chtrt5645/{HiFi,chtrt5645}.conf
sudo wget [https://raw.githubusercontent.com/pl...5645/HiFi.conf]("https://raw.githubusercontent.com/plbossart/UCM/master/chtrt5645/HiFi.conf") -O /usr/share/alsa/ucm/chtrt5645/HiFi.conf
sudo wget [https://raw.githubusercontent.com/pl...chtrt5645.conf]("https://raw.githubusercontent.com/plbossart/UCM/master/chtrt5645/chtrt5645.conf") -O /usr/share/alsa/ucm/chtrt5645/chtrt5645.conf 
[*]"blacklist snd_hdmi_lpe_audio" in /etc/modprobe.d/50-x205ta.conf 
[*]"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1 button.lid_init_state=open"" in /etc/default/grub
[LIST]
[*]does it need another command to work ? 
[/LIST]
  
[/LIST]
  
[/LIST]
To be honest, I have no more courage to read the X previous posts in search of answers for my issues (headphones, freezing, hibernation or suspend). If someone knows what to do, I would appreciate. 
If you think it's better to reinstall from one of harryharryharry's (stable) isos, I would understand and do it.
Many thanks in advance for any help.

kharshak

---

### Post by howefield on 2018-05-16
Post moved to its own thread and to the "*MINT*" forum.

---

### Post by kharshak on 2018-05-28
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1 button.lid_init_state=open"" in /etc/default/grub

[LIST]
[*]does it need another command to work ?
[/LIST]

Yes, I must have done a "update-grub".

---

### Post by kharshak on 2018-05-29
Some days ago, I decided to test one of the [harryharryharry's isos]("http://x205ta.myftp.org:1337/isos/")...

I installed [x205ta-harryskernel-4.15.0-rc7-sound-27-linuxmint-18.3-mate-64bit-UNTESTED.iso]("http://x205ta.myftp.org:1337/isos/x205ta-harryskernel-4.15.0-rc7-sound-27-linuxmint-18.3-mate-64bit-UNTESTED.iso")
Wifi goes well.
Then, I upgraded the kernel to 4.15.0-21. Some warnings (I don&#8217;t remember which) during the process, and grub was changed, so freezing was very frequent !!
So I redo the : "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1 button.lid_init_state=open"" in /etc/default/grub, followed by update-grub and things are now ok, no more freeze.

But sound was not working with this .iso (because of the iso or because of my poor understanding when upgrading the kernel&#8230; who knows ;).
So I redo the : 
sudo mkdir -p /usr/share/alsa/ucm/chtrt5645
sudo rm -rf /usr/share/alsa/ucm/chtrt5645/{HiFi,chtrt5645}.conf
sudo wget [https://raw.githubusercontent.com/pl...5645/HiFi.conf]("https://raw.githubusercontent.com/plbossart/UCM/master/chtrt5645/HiFi.conf") -O /usr/share/alsa/ucm/chtrt5645/HiFi.conf
sudo wget [https://raw.githubusercontent.com/pl...chtrt5645.conf]("https://raw.githubusercontent.com/plbossart/UCM/master/chtrt5645/chtrt5645.conf") -O /usr/share/alsa/ucm/chtrt5645/chtrt5645.conf

When I checked (before doing those commands), I only have a HiFi.conf file, no chtrt5645.conf&#8230; Maybe that was why sound was not working&#8230;

---

### Post by kharshak on 2018-05-29
Oh, and Bluetooth is also working. But I did not manage to have sound with my bluetooth headphones&#8230; Speakers only are ok.

---

### Post by kharshak on 2018-06-08
With another bt headphones, it's OK :)

---

### Post by bram-avontuur on 2018-06-10
Thanks for this thread. I have an Asus T102HA 2-in-1 which seems to be very similar to this, and this finally enabled me to get working sound.  I do have it working on both speakers and headphones. I used the volume mixer that came with lxde/openbox and set the correct corresponding output device.

---


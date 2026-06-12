---
title: "Can't get ubuntu working!"
date: 2004-10-30
forum: Installation &amp; Upgrades
---

### Post by vbouw on 2004-10-30
Hello,
I tried to install ubuntu * i386 release on my:
Athlon 2800  512 mb memory  Nviidea 256 mb

Everything goes well  also downloading updates etc.
The reboot ans of course I choose Ubuntu and then the problem begins!
After a few seconds of scrolling data I read:
 you got mail  and $ sign after the prompt!
Can't do nothing then to boot agiain!
I tried also linux acp=off but no reponse all the same as just boot ENTER
.
With SuSe 9.1 and Mandrake 10.0 and 10.1 no troubles at all, I had to install then by typing: load noapic and everything went smooth!
What can be the reason? I downloaded from Ubuntu website.
I got indeed the nessage x server not good, waht is the meaning of that?
I 'm working behind a router!
Vic

---

### Post by butters on 2004-10-30
Relax, you're at the command prompt... Ubuntu is installed but your X server (which creates the windowing environment) is misconfigured.  We need the following information to help you solve this problem:

Output of 'cat /var/log/XFree86.0.log'
Output of 'cat /etc/X11/XF86Config-4 | grep Driver'

You may need to install the nvidia driver

---

### Post by FLeiXiuS on 2004-10-30
[QUOTE=butters]You may need to install the nvidia driver[/QUOTE]

In that case,
Configure your /etc/apt/sources.list and add the universe repo.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-glx
sudo nvidia-glx enable

```

That should enable Nvidia's Drivers.

---

### Post by vbouw on 2004-10-31
Thanks for the comment!
But how or where can I find  OUTPUT of cat /var/log/XFree86.0.log?
And where do I have to type the commands:
sudo apt -get update etc etc.?
I'm new to Linux but have  using SUse 9.1 / Mandrake 10.0 /1 with a few problems due to my Geforce  fx5600 vard .
I also understand not that much english!  I'm dutch
regards,
Vic

---

### Post by liran on 2004-10-31
well,just write @ the bash shell (where you are at the moment)

cat /var/log/XFree86.0.log
cat /etc/X11/XF86Config-4 | grep Driver

and paste here,what you got.

---

### Post by vbouw on 2004-10-31
Well I will give it a try!
Vic

---

### Post by Rancoras on 2004-10-31
[QUOTE=liran]and paste here,what you got.[/QUOTE]

Make sure you paste the output inside "code" tags in your reply.  It just makes it easier to read.

---

### Post by vbouw on 2004-10-31
Well I tried but at the promt I just get:
You have mail  
$ 
And login /passw. not respondiing!
Maybe I will wait until Mandrake 10.1 ooficial is to be get?
This is frustating!
Vic

---

### Post by FLeiXiuS on 2004-10-31
I dont qutie understand what your getting.  Type:

```

passwd root

```

And tell me what you get.

---

### Post by vbouw on 2004-10-31
Ok I will retry it ince agiain!
regards,
Vic

---

### Post by vbouw on 2004-10-31
Well I tried again but still the same!
After installing ( all good ! )  still just txt scrolling and at the end:
I see: Ububtu 4.10 " Warty Warthog"ubuntu tty1
and then at the prompt:
ubuntu login:
So it is to become desperate lol!
I think it is the Geoforce 5600 card!
Problems with Xserver!
Do I have  the wright Ubuntu download?
I did an attachments with the Xserver  error I got.
Vic

---

### Post by FLeiXiuS on 2004-10-31
[QUOTE=vbouw]Well I tried again but still the same!
After installing ( all good ! )  still just txt scrolling and at the end:
I see: Ububtu 4.10 " Warty Warthog"ubuntu tty1
and then at the prompt:
ubuntu login:
So it is to become desperate lol!
I think it is the Geoforce 5600 card!
Problems with Xserver!
Do I have  the wright Ubuntu download?
I did an attachments with the Xserver  error I got.
Vic[/QUOTE]


Vic you have to install the nvidia drivers.  

Read up a few posts where I mention nvidia-glx.

---

### Post by vbouw on 2004-10-31
Well at the moment I'm back to Mandrake 10.0 official.
Here the install went smooth no troubles with xserver and my TFT Samsung 710v
But I will once try again Ubuntu  but how can I install those driver(s) if I can't go on because I will  be asked to give a password and nothing happens.
I tried the Dutch install and later on the English version but all the same problem!
Just passw. no good etc.
I probably will have a new 2 nd. HD coming week and will try again.
I just am surprised that Ubuntu ( new one) can't get through my geforce video card while installing Lubranet 2.81 also NO trobles!
On Mandrake 10.0 I jus have to type at the strt point after F1:
load noapic and everything goes excellent!
regards,
Vic

---

### Post by vbouw on 2004-11-01
Well I still wondering what can be the problem!
Maybe this:
Bios lookup I see: ACPI Compliant Bios
Could this be the error to the problems under Ubuntu?
Vic

---

### Post by obone on 2005-10-05
hé
i have tried to use ur method to solve my problem but still i recieve the same 
message
upon excute 


Output of 'cat /var/log/XFree86.0.log'
(**)  Option "SendCoreEvents" "true"
(**)  Synaptics Touchpad: always reports core events
(II)    XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II)   XINPUT:Adding extended input device "Configured Mouse" (type:Mouse)
(II)   Server_Terminate keybinding not found
SynapticsCtrl called
(II)Configured Mouse:ps2EnableDataReporting :succeeded
Sysnaptics DeviceOn called
(--) Synaptics Touchpad synaptics touchpad found
warning: font renderer for ".pcf" already registered at priority 0
warning ; font renderer for " .pcf.Z" already registered at priority 0
warning font renderer for ".pcf.gz" already registered at prioriry 0

warning font renderer for ".snf" already registered at prioriry 0

warning font renderer for ".snf.Z" already registered at prioriry 0

warning font renderer for ".snf.gz" already registered at prioriry 0

warning font renderer for ".bdf" already registered at prioriry 0

warning font renderer for ".bdf.gz" already registered at prioriry 0

warning font renderer for ".bdf.Z" already registered at prioriry 0

warning font renderer for ".pmf" already registered at prioriry 0

Could not init font path element unix/:7100, removing from list!
Synaptics DeviceOff called

(II) fglrx(0):[drm] removed 1 reserved context for kernel

(II) fglrx(0): [drm]  unmapping 8192 bytes of SAREA 0x0c42000 at 0x40236000


Output of 'cat /etc/X11/XF86Config-4 | grep Driver'
the result frm the output of the above command
Driver       "keyboard"
Driver       " mouse"
Driver       "synaptics"
Driver       " fglrx"


You may need to install the nvidia driver[/QUOTE]
i have again install the drivers for my nvidia driver but still the problem pertains
pls help me

---

### Post by obone on 2005-10-05
hi 
here under is the result
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT:Adding extended input device "Configured Mouse" (type:Mouse)
(II) Server_Terminate keybinding not found
SynapticsCtrl called
(II)Configured Mouses2EnableDataReporting :succeeded
Sysnaptics DeviceOn called
(--) Synaptics Touchpad synaptics touchpad found
warning: font renderer for ".pcf" already registered at priority 0
warning ; font renderer for " .pcf.Z" already registered at priority 0
warning font renderer for ".pcf.gz" already registered at prioriry 0

warning font renderer for ".snf" already registered at prioriry 0

warning font renderer for ".snf.Z" already registered at prioriry 0

warning font renderer for ".snf.gz" already registered at prioriry 0

warning font renderer for ".bdf" already registered at prioriry 0

warning font renderer for ".bdf.gz" already registered at prioriry 0

warning font renderer for ".bdf.Z" already registered at prioriry 0

warning font renderer for ".pmf" already registered at prioriry 0

Could not init font path element unix/:7100, removing from list!
Synaptics DeviceOff called

(II) fglrx(0):[drm] removed 1 reserved context for kernel

(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x0c42000 at 0x40236000


Output of 'cat /etc/X11/XF86Config-4 | grep Driver'
the result frm the output of the above command
Driver "keyboard"
Driver " mouse"
Driver "synaptics"
Driver " fglrx"


You may need to install the nvidia driver[/quote]
i have again install the drivers for my nvidia driv

---


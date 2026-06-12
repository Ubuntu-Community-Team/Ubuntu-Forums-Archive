---
title: "After (partial?) update, Ubuntu will not start"
date: 2018-09-06
forum: Installation &amp; Upgrades
---

### Post by jdkcarlson on 2018-09-06
Yesterday, Ubuntu told me it had some updates. I let them run in the background while I worked. Later, the computer ran out of battery. When I restarted, I saw I had more updates, so I decided to install them as well. It offered to upgrade the kernel to Bionic Beaver and I said yes. Some hours later I suspended the computer. 

This morning, when I opened the computer, not all the icons were showing on the log-in screen and I couldn't type. Usually if I can't type I suspend and unsuspend, but this time I could not suspend either. So I held down the power button to shut it down, which always feels like putting a baby to sleep by holding it underwater.

When I powered back up and attempted to boot normally, it never made it to the login screen. I get a black screen with just a movable arrow cursor. I powered off again and booted to recovery mode. I can't run fsck successfully, it seems, as it hangs indefinitely, but I had dpkg try to repair broken packages. However, when I try to revert to normal mode, I get the same black screen with just an arrow.

How can I get back into my OS?

---

### Post by Bashing-om on 2018-09-06
jdkcarlson; Were me ->

1st is to verify the file system from a liveUSB/DVD.
Then if the file system is consistent I would boot to a console interface at the login screen ( ctl+alt+F2 ) and check the graphic's driver status:
```

sudo lshw -C display

```

Depending on that result is what to do next.

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2018-09-07
I booted from a thumb drive and ran fsck -f. 
dev/sda1
where the EFI is 
and 
dev/sda7
which is the Ubuntu partition had block miscounts. 

Attempting to reboot normally, I see the reddish Ubuntu loading screen with the dots, but it still loads to a black screen with a movable arrow cursor but no login option. However, on this screen, ctrl+alt+F2 does work. 

On terminal log-in, I got this (my system is in Portuguese):

[https://imagebin.ca/v/4EvHBd8Xswpn](https://imagebin.ca/v/4EvHBd8Xswpn)

On doing sudo lshw -C display, I got this: 

[https://imagebin.ca/v/4EvIVQo54VuO](https://imagebin.ca/v/4EvIVQo54VuO)

Thank you.

---

### Post by Bashing-om on 2018-09-08
jdkcarlson - Humm ..

still appears to be a graphic's issue.

Integrated graphics ?
Please show:
```

lspci -k | grep -EA2 'VGA|3D'

```

[INDENT][INDENT]still an adventure in discovery
[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2018-09-09
Thank you!


00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
Subsystem: Acer Incorporated [ALI] Skylake GT2 [HD Graphics 520]
Kernel driver in use: i915_bpo

---

### Post by Bashing-om on 2018-09-10
jdkcarlson; Well,

That confirms we only have Intel for the graphics, The driver is loaded, so is this a config issue in your account ?

What release is this and what is the desktop that you are using ? Maybe see what results when activating a guest account ?

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2018-09-10
So is that good? 

The release is 18.04, upgrading apparently unsuccessfully from 16.04. I'm using an Acer laptop, Aspire R5-471T if that's what you mean, and if you meant desktop manager, I've been using Unity.

I haven't *gotten* to my account yet, in that I never make it to the login screen before it goes black; particularly, l don't think I could log in as a guest because I can't log in at all!

What would you recommend I do to diagnose or circumnavigate the problem?

---

### Post by Bashing-om on 2018-09-10
jdkcarlson; Yeah ..

All to the good that there is Intel for graphics.

unity is no longer installed by default. What you have now in 18.04 ubuntu is GDM3 or Wayland for the desktop.
Let's try:
```

sudo apt update
sudo apt full-upgrade
sudo apt install ubuntu-desktop

```

Advise of any reported errors, and if all looks good try and access a desktop.

[INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2018-09-11
When I try I'm told I can't connect to ca.archive.ubuntu.com, so I think I'm not connected to wifi. My work wifi uses PEAP and apparently makes it difficult to connect via the command line, so I will have to go somewhere else to connect to the wifi, apparently. I could try tethering my phone but I don't think I have the data to run a full upgrade

---

### Post by Bashing-om on 2018-09-11
jdkcarlson; Yuk -

WIFI is out of my experience range. A have to, however, is to make sure this system is fully up2date.

[INDENT]a firm foundation to push from
[/INDENT]

---

### Post by jdkcarlson on 2018-09-11
I've had great problems with wifi in the past. I don't know for sure this is the problem. However, when I run

dmesg | grep -e wlp -e net 

I get the following

[https://pasteboard.co/HDthD1d.jpg](https://pasteboard.co/HDthD1d.jpg)
[https://pasteboard.co/HDti0RJ.jpg](https://pasteboard.co/HDti0RJ.jpg)

which do not look so good. 

Again, I don't know how to update my system, especially without access to wifi. Is there a way to run the updates you suggest on my present partition whilst booting through a stick? This would at least enable me to separate the log-in and potential wireless problems into two distinct issues.

---

### Post by Bashing-om on 2018-09-11
jdkcarlson; Uh Huh -

> 
. Is there a way to run the updates you suggest on my present partition whilst booting through a stick? 

Short answer - yes.
The process is called a full change root and if this is a legacy install I can guide. EFI systems, I do not have the experience to be precise.
The procedure is not that tough but must be exact.
Show us the output from the liveUSB stick of terminal commands:
```

sudo blkid
sudo parted -l

```
so we know what the target(s) are.

Else can you come up with a wired internet connection to get the WIFI connection resolved ?

[INDENT][INDENT]trails, troubles and tribulations
[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2018-09-11
Never mind, I'm connected to wifi! The update and upgrade present new difficulties, which I will recount shortly

---

### Post by jdkcarlson on 2018-09-11
I've gotten through a log-in! The only real errors in the update have to do with being unable to locate repositories and with grub, which it says it will not update due to unsigned certificates.

I'm told, now that I'm logged in, that no wifi adapter is available however, so I guess that is the beginning of another process.

---

### Post by Bashing-om on 2018-09-11
jdkcarlson; Progress made !

We do need to see those outputs.
show - Between code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt full-upgrade

```


[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by jdkcarlson on 2018-09-12
Hi Bashing-om, sorry for missing one of your messages. My email didn't notify me in a timely way and I didn't see it because it was on Page 2 of this thread. The old errors with update and full-upgrade -f (without -f it had more problems) were respectively the following:

[https://pastebin.com/Y4B5z5hT](https://pastebin.com/Y4B5z5hT)

and

[https://pastebin.com/yT85QTth](https://pastebin.com/yT85QTth) ;

my apologies for what seems to be an encoding problem in the second output. 

Moreover, I got the following error screen: 

[https://imagebin.ca/v/4FTID2rqs9jq](https://imagebin.ca/v/4FTID2rqs9jq)

The cut-off text at top is "or replaced with signed kernels"

Since the wifi wasn't working either, I USB-tethered my phone and did what Jeremy31 suggested in the thread

[https://ubuntuforums.org/showthread.php?t=2392454](https://ubuntuforums.org/showthread.php?t=2392454),

namely,

```
sudo apt remove bcmwl-kernel-source && sudo apt install git dkms
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

This got me wifi back. It told me that I could update my GRUB, which had changed, or stick with my local copy. It was an option to merge versions, but it told me doing that would lead to errors, so I kept my local copy. I had to put in a Secure Boot code to continue the dkms process.

```
sudo apt update
```
no longer gives errors.

```
sudo apt full-upgrade
```
installed 5 new packages and updated 45.

But it stopped at 75% and my computer froze. I couldn't do alt+prtsc+R E I S U B, so I turned it off by holding down the power. When I turned it back on, neither update nor full-upgrade gave errors, and they said everything had been completed.


I've also been trying to repair Bluetooth and my trackpad's sensitivity, which are broken again in this version. It seems that every time I use dkms, I have needed to set a code for Secure Boot again. However, I'm not sure whether this is just because I haven't had a normal shutdown yet.

---

### Post by Bashing-om on 2018-09-12
jdkcarlson; And .. 

Now all good less bluetooth and the trackpad ?
Updates for trackpads are in the pipeline that address several issues such as sensitivity :)

[INDENT][INDENT]maybe light at the end of this tunnel
[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2018-09-15
I'm getting a lot of crashes from Chrome, many more than I did with Xenial. If I open too many tabs, things slow to a crawl, clicks are registered only intermittently, or their receipt is delayed, and there is only a small window during which I can close Chrome or Alt+PrtSc+REISUB will work to shut down the computer. After this window I am forced to hold down the power key. I also haven't been successful with right clicks yet (I installed something that supposedly enables me to either click in the bottom-right of the trackpad or two-finger-click, but after a suspend and desuspend, I find I cannot right-click at all), and the search function one reaches by hitting the Meta key fails to locate the overwhelming majority of my files. 

I'm frustrated because Bluetooth was also broken in Xenial, and it required a specific and counterintuitive technique to connect at all for a year or two until they finally fixed it, and apparently nothing was learned in the interim. But I'm absolutely never going back to Windows or Mac, so ¯\_(&#12484;)_/¯

---

### Post by Bashing-om on 2018-09-15
jdkcarlson; Hey ..

Sounds like just not enough memory to do all that you want done at once.

when the system is loaded up what shows:
```

free -m

```

is swap being hammered ?
Maybe a lighter desktop is the answer here ??

[INDENT][INDENT]only maybe - only
[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2018-09-15
[FONT=Courier New]              total       usada       livre    compart.  buff/cache  disponível
Mem.:          7858        5413         380         705        2064        1438
Swap:           487         395          92
[/FONT]

However I've bookmarked the open Chrome tabs and have only five open now. I am running one instance of Firefox with seven tabs as well, and have about four PDFs open in the default document viewer, and one file in Gedit. That's it for processes visible without using the command line.

---

### Post by Bashing-om on 2018-09-15
jdkcarlson; Yuk .

Out of my direct skill set now, but, something is really eating up the memory .. and swap is hammered.
Maybe time to learn 'top' and see where the resources are going ?

[INDENT][INDENT]an 8 pound sack should hold a lot[/INDENT][/INDENT]

---

### Post by jdkcarlson on 2018-09-23
Bashing-om,

top > top.txt produces a misencoded document, so I'll attach a picture.

[https://imagebin.ca/v/4GjcpcZXRKcP](https://imagebin.ca/v/4GjcpcZXRKcP)

This wasn't a particularly bad time when I ran top, though; when it freezes, I typically can't navigate to a terminal or type anyway, so I'm not sure how to diagnose the problem.

---

### Post by Bashing-om on 2018-09-23
jdkcarlson; Well .. 

A book can be written on what I do not know about 'top', but, - not knowing how many CPUs you have - the load average looks real high to me. Else all looks good.

[http://tecadmin.net/understanding-linux-top-command-results-uses/#](http://tecadmin.net/understanding-linux-top-command-results-uses/#)
[https://linuxaria.com/howto/understanding-the-top-command-on-linux](https://linuxaria.com/howto/understanding-the-top-command-on-linux)


[INDENT]if I knew better
[INDENT][INDENT]I would do better
[/INDENT][/INDENT][/INDENT]

---

### Post by jdkcarlson on 2018-09-24
Thank you, Bashing-om! What would be the appropriate forum for fixing these memory issues?

---

### Post by Bashing-om on 2018-09-24
jdkcarlson; Well -

" General Help" should be appropriate and get a wider view . Just open a new thread on this issue .

[INDENT]like dead men - threads
[INDENT][INDENT]one to a box
[/INDENT][/INDENT][/INDENT]

---


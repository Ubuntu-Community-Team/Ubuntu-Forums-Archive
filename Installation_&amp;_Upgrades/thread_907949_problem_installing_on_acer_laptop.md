---
title: "problem installing on acer laptop"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by dis_space on 2008-09-02
hi all.
i've just got an acer 4530 (AMD Turion 64 X2 2 Ghz, geforce 9100M G, 4 GB RAM)recently and i'm trying to install ubuntu on it since it didnt have any OS installed, but it does have a DOS like linux linpus.
i tried to install ubuntu on my laptop but it is problematic.
here's what i've done :
downloaded,win5md'd,and burned ubuntu
at the ubuntu startup screen, checked the CD for errors, checked the RAM.
when i tried to install (same goes with trying without install), the screen moves to a black background with an ubuntu  logo, followed by an 'UBUNTU' and below we got the progress bar.
it stopped progressing at about 10 percent.
i've tried all_generic_ide floppy=off irqpoll;noacpi;noapic nolapic
without any progress
i even redownload it again but its not that
what to do guys?
pls help

---

### Post by Partyboi2 on 2008-09-02
When you are at the main menu can you press F6 and change splash to nosplash this will remove the loading bar (splash) and hopefully will display where it is freezing at.

---

### Post by Caveira2099 on 2008-09-02
If you search for "acer 4530" here at ubuntuforums you'll see another post where I pointed the same problems as you. I am working on it, and I really need a fast solution, my work is stopped!

Well, it still freezes with me too. The only progress I have so far is the fact that OpenSolaris 2008.05 boots but fails to load all network and graphics drivers.

I read in a foreign site (I don't remember which one, I was looking at ALL google results for "acer 4530 linux") and the guy said he could boot after "removing" the wireless card and using the same boot options you mentioned... I am not willing to try this, and without wireless, it is basicall the same for me.

If only I could boot and install the very latest nvidia drivers (177 I think...)...

Let's keep these threads open until we find a solution.

---

### Post by Caveira2099 on 2008-09-02
Oh I forgot to write down the boot:

```

Loading hardware drivers...
[139.557909]
[139.557910] HARDWARE ERROR
[139.557910] CPU 0 : Machine check exception 4 bank 4:b60000000007f0f
[139.558120] TSC 3dd8997f49 ADDR 900000ca404001
[139.558277] This is not a software problem!
[139.558346] Run through mcelog --ascii to decode and contact your hardware vendor
[139.558438] Kernel panic - not syncing: Machine check

```

---

### Post by Dogmeat on 2008-09-03
Caveira, I bought the same machine (Acer Aspire 4530-5267) recently and I had the same problems trying to get Ubuntu 8.04 working on it. I tried several ubuntu cds, even ultimate edition, 32-bit, 64-bit, you name it. I always got either that error or a kernel panic. My last attempt was trying Ubuntu 8.10 32-bit alpha 4, and to my surprise it worked! 

I'll share my experience with Ubuntu (above version) on this notebook:

- At first, the wireless driver won't work, but if you connect an ethernet cable, apt-get update, upgrade, and dist-upgrade, and boot into the 2.6.27 kernel it will work. If it doesn't, try pressing the wireless key (the led won't light but the button works). For me it stops working after suspend/hibernate, but a iwconfig wlan0 channel 1 and iwlist wlan0 scanning "wakes up" the connection.

- The display works great after you install the NVIDIA drivers, version 173. The 177 version didn't give me 2d acceleration.

- The keyboard is almost perfectly autodetected. Almost every key I tried works, except for the bluetooth one (no problem since this model doesn't come with BT, and the Euro and Dollar key near the cursors)

- Suspend and hibernate work, but to resume successfully I had to add floppy=off and pci=nomsi to the kernel parameters on boot

- Sound doesn't work at first, but it does after the dist-upgrade (kernel 2.6.27).

- The card reader works sometimes, sometimes it stops working, but this also happens on windows. If you turn on the computer with a card inserted it will always work, at least until you remove and insert the card again.

- The mic works fine (kernel 2.6.27).

- The webcam works fine (tested with kernel 2.6.27).

Overall I was pretty impressed with this level of support, considering I couldn't even boot several linux versions. Intrepid seemed relatively stable for an alpha. However if you're not confortable using alpha versions, I recommend you try Ubuntu 7.10 32-bit, I tried it and it goes to the X safe-mode on installation, but I suspect it will be harder to make everything work since it's a bit outdated, and this notebook is pretty new.

The sad part is my touchpad simply stopped working on every OS. The OS doesn't even know it's there, so I suspect its a hardware fault, and I sent it for repairs. And yes, I tried Fn-F7 and removing the battery. When it comes back I can use it a bit more and share some more experiences.

---

### Post by Caveira2099 on 2008-09-03
Thank you a lot Dogmeat!

My system is half usefull with windows. I have tested everything to be sure that the hardware is ok. I'll surelly try the alpha.

And I think you answered the most important question that I had: the problem is really with the lack of proper driver and of kernel support. I might try something else than ubuntu with 2.6.27 and I'll also share my discoveries.

Thanks again!

Cheers

---

### Post by Caveira2099 on 2008-09-08
Time for updates.

Dogmeat was right, the combination of the linux kernel 2.6.27 and the latest Nvidia drivers do work. I am actually writing this reply from a live session with Mandriva 2009 RC1.

Some remarks:

1- The 177 Nvidia beta drivers do not provide 2d acceleration indeed;
2- With Mandriva 2009 RC1 the screen resolution is set to 1024x768;
3- Every hardware seems to work just fine;
4- The dollar and euro keys, volume mute and volume wheel do not work;
5- Screen brightness keys, Fn+F7 (touchpad toggle) do work.

This is out-of-the-box support, without boot parameters and without any updates, just the latest plain iso. I still haven't tested suspend and hibernate, and the wireless keys (I'll test as soon as finished writing this reply :P ).

The 2.6.27 kernel is mandatory, for it adds support for the motherboard - the main reason for kernel panics in older versions - as it "wrapps" the nvdia motherboard SATA/IDE, audio and other stuff as if it was intel's motherboard. Check [www.kernel.org](www.kernel.org) for more details.

Conclusion: it's just a matter of time for linux support by this laptop - it'll happen as soon as linux 2.6.27 based distros are officially released.

No, I don't plan to install an alpha, beta or RC stage distro on my laptop. I don't exactly have the time to wait, but I feel better waiting than installing unstable releases that will soon be updated to mainstream.

I am downloading alpha 5 of Intrepid, I'll post my experiences with it ASAP.

Thank you guys and please send any comments/experiences with any distro, please.

---

### Post by Caveira2099 on 2008-09-08
More info:
 
6- The wireless toggle key works and the connection is recovered normally after on/off/on procedure;
7- Screen resolution 1280x800 can be easily set on mandriva control panel (using it now);
8- Seems to be capable of configuring all keys not recognized at first;
9- Network adapters work flawlessly out-of-the-box
10- Video card and sata controlers are loaded in sub-optimal compatibility mode (video as 6100m or later and sata as generic nvidia MB controller);
11- Infocenter points an unknown devide (nvidia coprocessor) and the rest (mic, webcam) is working.

---

### Post by Caveira2099 on 2008-09-09
Dogmeat, I am now trying Intrepid Alpha 5 64bit but I can't make it boot. Something is going on with the hardware detection scripts.

Can you post all the boot parameters you had to use in order to boot alpha 4 32bit?

---

### Post by jzerbini on 2008-09-10
> **Caveira2099 said:**
> Dogmeat, I am now trying Intrepid Alpha 5 64bit but I can't make it boot. Something is going on with the hardware detection scripts.

Can you post all the boot parameters you had to use in order to boot alpha 4 32bit?

I was following quietly this whole thread, and now I felt like writing my own post :)

EXACTLY the same things happened here. I downloaded Intrepid 32 and 64 bits, burnt it 3 times, without success.

The only distribution I was able to boot was openSUSE 11 (64 bits), but no sound, no webcam and no wireless were available.
I didnt test the 2.6.27 kernel, though. They don't have it (or at least I didnt find it available to download) and I didnt feel comfortable compiling my own kernel.

Btw, I'm also brazilian ;]

---

### Post by jzerbini on 2008-09-10
Updated: The 32 bits version of the Intrepid DOES BOOT without any extra parameters.

I have the Acer Aspire 4530-5267 that comes with the Athlon X2 processor, not the one with the Turion CPU.

I'm checking right now if it detects the wireless card, the webcam and the soundcard.
Will update this ASAP.

(I wanted the 64 bits version, though... :( )

---

### Post by jzerbini on 2008-09-12
Little update:

Intrepid 32 bits works almost smoothly.

I just had to blacklist ath5k and install the ath_pci modules to my wireless adapter work perfectly.
Sound, Ethernet, Nvidia card, and touchpad mouse are 100%.

A couple of hours ago I did an apt-get upgrade that installed some new gnome packages. That broke Gnome partially, but not a big deal. I could start using fluxbox once again ;] That's what Alpha sofware means afterall, isnt it.

Let's hope we have another gnome update by tomorrow that fixes the thing. (I also had a kernel panic while inside gnome. Probably because of the wireless driver, need to recompile).

Thanks !

Edit: Could one of the moderators (or the original owner) rename the title of this thread to have the Model of this acer laptop ?
I bet google would love this.

---

### Post by Dogmeat on 2008-09-14
Caveira, I didn`t use any parameters to boot, and I didn`t try the 64-bit version of Intrepid. My notebook is also the one with the Athlon X2 processor, and the exact version that worked is the Intrepid Ibex (8.10) alpha 4 32-bits. I didn`t try alpha 5 or anything else since my last post on this thread, because my notebook is still being repaired. I wonder if the alpha 5 will make the 4530 work out of the box? I suspect the 32-bit version will work, not sure about the 64-bit one.

---

### Post by teguh.umar on 2008-09-18
> **jzerbini said:**
> Little update:

Intrepid 32 bits works almost smoothly.

I just had to blacklist ath5k and install the ath_pci modules to my wireless adapter work perfectly.
Sound, Ethernet, Nvidia card, and touchpad mouse are 100%.

A couple of hours ago I did an apt-get upgrade that installed some new gnome packages. That broke Gnome partially, but not a big deal. I could start using fluxbox once again ;] That's what Alpha sofware means afterall, isnt it.

Let's hope we have another gnome update by tomorrow that fixes the thing. (I also had a kernel panic while inside gnome. Probably because of the wireless driver, need to recompile).

Thanks !

Edit: Could one of the moderators (or the original owner) rename the title of this thread to have the Model of this acer laptop ?
I bet google would love this.

Can you teach me how to blacklist the ath5 before install?

---

### Post by jzerbini on 2008-09-22
> **Dogmeat said:**
> Caveira, I didn`t use any parameters to boot, and I didn`t try the 64-bit version of Intrepid. My notebook is also the one with the Athlon X2 processor, and the exact version that worked is the Intrepid Ibex (8.10) alpha 4 32-bits. I didn`t try alpha 5 or anything else since my last post on this thread, because my notebook is still being repaired. I wonder if the alpha 5 will make the 4530 work out of the box? I suspect the 32-bit version will work, not sure about the 64-bit one.

It will [almost] work. Wireless won't work with the native ath5k drivers.
You'll have to compile and load this specific module to get wireless working:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

It's very easy.. Just make && make install, blacklist ath5k and voilá ! Everything's working !


> **teguh.umar said:**
> Can you teach me how to blacklist the ath5 before install?

Absolutelly, Sir !

Just open /etc/modprobe.d/blacklist and add the **ath5k** at the last line of the file.
Or if you're lazy (like me ;]) just run this command:

```
sudo echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
```

:popcorn:

---

### Post by gootoo on 2008-09-23
yes, 64bit SuSE 11 works fine, except sound, webcam and wireless.
But still do not know the reason why Ubuntu can not boot.
If anyone know this, please post the update.
thank you very much.

---

### Post by Caveira2099 on 2008-09-25
Hi guys,

The problem lies in the kernel. 2.6.27 will work almost perfectly, and I hope that nvidia releases a driver to fix whatever does not work.

The issues are due to lack of kernel support. From 2.6.26.5 and on the kernel gurus have made an ugly repair - the kernel uses intel commands to communicate with this nvidia mobo.

As long as I needed Scientific Linux working, I had to keep windows and use virtualbox. It is far from what I really need, but it's ok until the 2.6.27 based distros are out.

OpenSuse has become a serious alternative for me, but maybe I'll give opensolaris 2008.10 based distros a try.

Let's keep this thread live until we are 100% with our hardware!

Cheers,

P.S. I am from Rio de Janeiro, ubuntuforums isn't updating my info for some unknown reason...:lolflag:

---

### Post by fserve on 2008-09-26
my laptop is running ok with Alpha 6 + updates. (32bits)

only the card reader isn't working right now.
for webcam i've tested with cheese, so it's ok.

wifi i'm using MadWifi HAL:

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

Video with driver v173 but some glitchs appears on the screen sometimes...

Sound is ok, workin out of the box, mic too

I'm from Manaus - Brazil ;)

---

### Post by Dogmeat on 2008-09-26
> **fserve said:**
> my laptop is running ok with Alpha 6 + updates. (32bits)

only the card reader isn't working right now.
for webcam i've tested with cheese, so it's ok.

wifi i'm using MadWifi HAL:

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

Video with driver v173 but some glitchs appears on the screen sometimes...

Sound is ok, workin out of the box, mic too

I'm from Manaus - Brazil ;)

Well I finally got my Aspire back from repairs, I'm also using that same version with those modifications (except now I'm using nvidia v177. I'll explay why below). I fixed some more stuff that was pending: 

NOTE: The parenthesis after the fixes refer to the respective files that fix it. I included mine in the attached zip.

 - Added some keycodes that were missing, such as the bluetooth key and the first key (the one that looks like \o/), over the wireless LED, and fixed the keyboard € and $ keys beside the cursor keys (/etc/keys.map, /etc/loadkeys.sh, /etc/init.d/bootmisc.sh)

- Blacklisted ath5k because it only worked sometimes, and added madwifi, and some special commands to make the led blink.  (/etc/rc.local, /etc/modprobe.d/blacklist, download and compile madwifi from [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/) (I used the 03/09/08 version))

- Added the madwifi modules to DKMS so new kernel upgrades will compile and install this module automatically (/usr/src/madwifi-hal-0.10.5.6-r3861-20080903/dkms.conf)

- Added a script to remove and reload the madwifi module when hibernating/suspending so the wireless connection will work automatically after hibernate (/etc/pm/sleep.d/wireless).

Issues that remain:

- The card reader worked sporadically before in alpha 4 with updates. Now I never got it working again, not sure if I`ve been unlucky or some upgrade caused it to stop working altogether. However, this card reader doesn`t work properly in XP either, maybe it only works properly on vista only at the moment? can someone with vista installed verify this?

- The nvidia driver 173 doesn`t give me 3d acceleration for some reason. And 177 doesn't give me 2d acceleration. I'm sitcking with 177 since I play some games. I also found this tweak which makes it usable (except for some 2d games): 

Partial fix: create a script that runs everytime you login on X. It should contain this:
```
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1
```
It should now be usable. If you still think it's too slow, enable compiz with light effects.

- Suspend works partially with pci=nomsi kernel parameter, but gives a kernel panic and the sound becomes weird. The system becomes unstable and some programs start to die, so I'm not using suspend for now

Besides these issues, my notebook is working perfectly with ubuntu 8.10. Very stable for an alpha. I'll now attach the files I mentioned above, they`re in a zip file. You can extract them to the paths I mentioned above to apply my fixes to your 4530. However if you modified any of them you should make backups first, then merge them.

---

### Post by fserve on 2008-10-04
i'm using 177 now, very better then 173.x

and i think that i have 2d aceleration, how i can test it?

compiz is running ok, glx gears too, games too...

---

### Post by Caveira2099 on 2008-10-07
Hi all!

Dogmeat, again, thanks a lot! If we can get it working on alphas and betas, it has a great chance to work fine with the final 8.10.

1) I still have vista :( on my acer, and the card reader is 100% ok. I have never experienced the issues you posted...

2) We had recent updates on the 2.6.27 kernel, maybe the final release will give us a good surprise. They are working explicitly on kernel support for this mobo/chipset.

But all these will not help with the ath5 driver, or the keyboard unmapped keys. So, if any of you guys know how to do it, we should tell somebody to add these features to the next ubuntu release, just like they have done to many laptops.

Cheers!

P.S. Valeu galera!!! Parece que esse laptop tá famoso no Brasil.... hehehehe:lolflag:

---

### Post by Dogmeat on 2008-10-10
> **Caveira2099 said:**
> Hi all!

Dogmeat, again, thanks a lot! If we can get it working on alphas and betas, it has a great chance to work fine with the final 8.10.

1) I still have vista :( on my acer, and the card reader is 100% ok. I have never experienced the issues you posted...



Caveira, does your card reader work on Ubuntu too? Even if you insert, remove, and insert the card again, it works all the time?
I think a lot of devices are connected internally via USB. I may have a USB issue here because once the external mouse stopped working on linux, so I went to try it on XP and it still wasn't working, then it came back out of nowhere. Today the same happened with the webcam. The card reader is USB too so it looks like there are some USB issues, I just don't know if it's a problem with the kernel, or my notebook is faulty. Can you please try to use the memory card as I described above with all the Intrepid updates? You're using the 32-bit version right?

Thanks!

---

### Post by Caveira2099 on 2008-10-10
Hi Dogmeat!

I do believe it is a USB issue, instead of your system being faulty. I still haven't tested, but I believe that you have to manually unmount the card before removing it. I had similar problems with my previous notebook, and every time I wanted to remove my card, I had to open nautilus and unmount it.

Try that first, and then I'll check Ubuntu, I don't think I'll be able to do it for the next couple of days :)

Cheers,

---

### Post by teguh.umar on 2008-10-13
> **jzerbini said:**
> It will [almost] work. Wireless won't work with the native ath5k drivers.
You'll have to compile and load this specific module to get wireless working:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

It's very easy.. Just make && make install, blacklist ath5k and voilá ! Everything's working !




Absolutelly, Sir !

Just open /etc/modprobe.d/blacklist and add the **ath5k** at the last line of the file.
Or if you're lazy (like me ;]) just run this command:

```
sudo echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
```

:popcorn:

Thanks for the lesson, but how to disable the ath5k at first ubuntu installation? Sory, I'm new in linux world, and want to take the MS retired at my new-old machines

---

### Post by fserve on 2008-10-15
Well, the driver 177.x isn't giving me 2D aceleration... very buggy : (

but wow, thank you for those files, dogmeat

you forgot the file 'loadkeys.sh' or it is the 'keycodes.sh' ?

my card reader is working ok.

sometimes my laptop yells at the ubuntu boot, do you guys have that?

i love dkms :)
very thank you.

---

### Post by dreamsong on 2008-10-24
hello. :)


been trying to install the intreprid beta on my 4530 as well, but
it has an error during installation.

first it goes on low graphics mode warning:
(EE) device not found. then it goes into a selection menu where you 
can pick something like a)use default b)use new setting c)used saved setting...

every option just seems to go back to that choice menu.
even resetting afterwards, it just goes back to the same menu.
does anyone know how to solve this problem?
it'll be much appreciated :)


p.s. i'm a real ubuntu / linux newbie. previous experiences was
just installing hardy on older laptops which worked great out
of the box. haven't done or know anything fancy yet on the terminal
except a few get-apps. 

acer 4350 (bio sensor variant)
2.0 amd turion x2
2gig ddr2 ram
nvidia geforce 9100M G


thanks!

---

### Post by gootoo on 2008-10-24
> **Dogmeat said:**
> Caveira, I bought the same machine (Acer Aspire 4530-5267) recently and I had the same problems trying to get Ubuntu 8.04 working on it. I tried several ubuntu cds, even ultimate edition, 32-bit, 64-bit, you name it. I always got either that error or a kernel panic. My last attempt was trying Ubuntu 8.10 32-bit alpha 4, and to my surprise it worked! 

I'll share my experience with Ubuntu (above version) on this notebook:

- At first, the wireless driver won't work, but if you connect an ethernet cable, apt-get update, upgrade, and dist-upgrade, and boot into the 2.6.27 kernel it will work. If it doesn't, try pressing the wireless key (the led won't light but the button works). For me it stops working after suspend/hibernate, but a iwconfig wlan0 channel 1 and iwlist wlan0 scanning "wakes up" the connection.

- The display works great after you install the NVIDIA drivers, version 173. The 177 version didn't give me 2d acceleration.

- The keyboard is almost perfectly autodetected. Almost every key I tried works, except for the bluetooth one (no problem since this model doesn't come with BT, and the Euro and Dollar key near the cursors)

- Suspend and hibernate work, but to resume successfully I had to add floppy=off and pci=nomsi to the kernel parameters on boot

- Sound doesn't work at first, but it does after the dist-upgrade (kernel 2.6.27).

- The card reader works sometimes, sometimes it stops working, but this also happens on windows. If you turn on the computer with a card inserted it will always work, at least until you remove and insert the card again.

- The mic works fine (kernel 2.6.27).

- The webcam works fine (tested with kernel 2.6.27).

Overall I was pretty impressed with this level of support, considering I couldn't even boot several linux versions. Intrepid seemed relatively stable for an alpha. However if you're not confortable using alpha versions, I recommend you try Ubuntu 7.10 32-bit, I tried it and it goes to the X safe-mode on installation, but I suspect it will be harder to make everything work since it's a bit outdated, and this notebook is pretty new.

The sad part is my touchpad simply stopped working on every OS. The OS doesn't even know it's there, so I suspect its a hardware fault, and I sent it for repairs. And yes, I tried Fn-F7 and removing the battery. When it comes back I can use it a bit more and share some more experiences.

hi friend, have test 64bit ubuntu810?
my side cannot boot.

---

### Post by Caveira2099 on 2008-11-05
For those who want some updates on the 64bit front...

I am posting from a working OPENSUSE 11.1 Beta4 Gnome Live cd!!!

Boots nicely, without need for disabling acpi or the rest. Just press enter at startup and that's it!

I am using the Vesa driver for (in)convenience, but as it loaded and launched my wireless card perfectly, it is just a matter of downloading and installing the official Nvidia driver for Suse Linux.

Wonderful. I have just tried Fedora Rawhide (last preview before Fedora 10 Cambridge) and it failed to boot both 32 and 64 bit versions.

Sorry to all, but I'll go with OpenSUSE from now on.

OpenSUSE 11.1 AMD64 = Working!!!

Cheers,

---

### Post by LashSilence83 on 2008-11-30
How exactly did you get openSUSE to boot ? I've tried booting the 11.1 rc1 gnome beta 4 x86_64 live cd with various boot options and none of them seem to let me do much more than get a running kernel and bash shell. It always says "failed services in runlevel 5" and won't in any way let me start the x server. It also throws a lot of other errors before dropping me at a login prompt. I'm starting to think buying this laptop was a massive mistake...

---

### Post by Caveira2099 on 2008-11-30
Hi, are you sure you got the RC1 of 11.1 from [http://software.opensuse.org/developer](http://software.opensuse.org/developer) ?

Well, since Beta 5, OpenSUSE booted without any sort of extra boot options, I just did the default (boot and press ENTER)...

If you are sure you got the right version, please post exactly what error messages you get and I'll try to figure it out.

Cheers,

---

### Post by LashSilence83 on 2008-11-30
Here's something else I just noticed... If I install 8.10 intrepid 32 bit by going through the straight "install" option on the live cd, I get the insane beeping when I reboot. However, if I boot into the live environment and then run the install from there, there is no beeping on reboot. Maybe it's just me, but I find this quite strange...

---

### Post by Caveira2099 on 2008-11-30
It is something odd, but its origins are in the init scripts - those responsible of calling the services during the boot. When this bug was first found, the live cds wouldn't boot, but the alternate install would.

The strangest thing is that 32bit behaves quite different of 64bit - I still can't boot Ubuntu x64 on this laptop, that's why I have gone with OpenSUSE.

I've found that OpenSolaris also boots, and it does really a nice job - everything works, and it loads the default Nvidia official drivers. I just don't want to change to a whole different userland yet...

---

### Post by Caveira2099 on 2008-11-30
Maybe I have not been clear enough when I said about openSUSE...

I am writing this very post with the 11.1 RC1 Gnome Livecd x86_64 with the default boot options.

Wireless card, camera, video, everything OK. Even the sound wheel works great!

Once again, if you don't feel like trying openSUSE, try OpenSolaris 2008.11 then. It's as stable ans usable as openSUSE, but with Unix userland instead of linux, so don't ask me about those weird devices at /dev :)

Cheers,

---

### Post by Killer_B on 2008-11-30
> **Caveira2099 said:**
> Maybe I have not been clear enough when I said about openSUSE...

I am writing this very post with the 11.1 RC1 Gnome Livecd x86_64 with the default boot options.

Wireless card, camera, video, everything OK. Even the sound wheel works great!

Once again, if you don't feel like trying openSUSE, try OpenSolaris 2008.11 then. It's as stable ans usable as openSUSE, but with Unix userland instead of linux, so don't ask me about those weird devices at /dev :)

Cheers,

Mandriva ONE 2009 liveCD boot has had everything working on my AS4530-5627; Ethernet, wireless, video, sound...All pretty much are working. Perhaps once I get more time to tinker with it, I can move onto checking how the webcam/etc. work with it.

---

### Post by LashSilence83 on 2008-11-30
Sorry it took me so long to reply Caveira2099, seems that I couldn't reach the forums earlier today. Upon your mention of opensuse 11.1 beta 5, I began downloading it so I can give it a try. Also, I did try openSolaris 2008 and it booted fine and seemed to work alright with the exception of there being no network drivers (wired or wifi). Right now I'm using intrepid 32 bit with ndiswrapper and it's working alright with the exception of no webcam and suspend/hibernate causes a crash. I'm still debating whether I should keep trying other distros or just wait for ubuntu fixes. 

one other thought: what is the deal with the proc on this laptop? I was beginning to think that it wasn't really 64 bit until I got the 64 bit opensuse to boot. Even if it's just the command line, it still proves that it does work on this laptop. :confused:

---

### Post by LashSilence83 on 2008-11-30
update: I tried to boot the mandriva one 2009 gnome cd, and I got an error: 

"kernel panic- not syncing VFS:unable to mount root fs on unknown-block"
I also tried the openSUSE 11.1 beta 5 cd and it was worse than beta 4 in that it just stopped at the splash screen and would go no further no matter what parameters I tried to pass at boot. What is it about this laptop that poses such a problem? :confused:

---

### Post by Caveira2099 on 2008-12-01
Dude, something is really wrong here... OpenSUSE and Mandriva boot fine here. Really make sure you get the latest development version. I really would like to see if your hardware is exactly the same as mine.

And the cpu is x64 capable. And didn't you notice that OpenSolaris 2008.11 chose 64bit automatically?

If you can, send in some hardware info.

Cheers,

---

### Post by LashSilence83 on 2008-12-02
How about an lspci and lshw readout for starters? Hope these help...

btw: yes, I did notice that solaris chose 64 bit automatically. This further confused me since many other 64 bit distros wouldn't boot at all. It's just weird.

---

### Post by nikolaiortiz on 2008-12-03
HI to all..
I got a acer aspire 4530.
i'm install intrepid, kubuntu.
All hardware work fine out of the box, the nvidia 180.11 beta driver works good..
but the sound is bad i mean..
the sound works but not work on firefox for flash, not work skype, and no work for amsn.
the sound problem is really annoying please some help.
thanx

---

### Post by russell5 on 2008-12-05
I got a 4530 and i love the laptop but the nvidia support on Ubuntu 8.10 was crappy. Couldn't even run AWN. I saw the last post about the beta nvidia driver working ok. So i installed version 180.06 and it runs awesome. Fixed all my graphics issues i was having.
Thanks

---

### Post by KEE on 2008-12-05
yeah i have the same problem with my acer laptop =(

---

### Post by LashSilence83 on 2008-12-06
I wonder if there is any way at all that I could get the webcam to work... Also, I still can't figure out the exact reason why inrepid 64 bit won't install, or much less even boot on this laptop.

---

### Post by nikolaiortiz on 2008-12-06
HI.. lashsilence

did you try to change the sata setting on bios?.. switching to hda mode..?

my ubuntu boot fine using this to install.. and after that i change again to sata and work fine.. 

all things works fine out of box.. i recommend to use the latest nvidia driver 180.11
cheers

---

### Post by LashSilence83 on 2008-12-06
I just tried that and it didn't change anything. intrepid 64 bit gets to about 10% at the boot splash and then the machine has a kernel panic indicated by the flashing caps lock light. This is really annoying...

---

### Post by Killer_B on 2008-12-08
here's a suggestion--


Perhaps give the memtest option a try.

If it comes back with errors, it could be the memory.

---

### Post by LashSilence83 on 2008-12-08
ok, I just ran the memtest without any problems. Maybe It has something to do with the two different models. There's a turion model and an athlon model. I have the athlon model. Perhaps that is the issue. I have no idea why it would be, but it's worth looking into.

---

### Post by nikolaiortiz on 2008-12-08
Umm what kernel panic?
post if you can :)

---

### Post by LashSilence83 on 2008-12-08
With most live cd's I'm getting an error stating: 
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,6) 

Could it be that all of the cd's I'm burning are corrupted in some way and that would be the reason why this isn't working? I guess that might make sense but then again it wouldn't because the 32 bit intrepid cd I installed with was made on the same machine that's burning all these others.

---

### Post by nikolaiortiz on 2008-12-08
umm.. i see some tips here..
[http://kerneltrap.org/node/7053](http://kerneltrap.org/node/7053)

but look like is a big problem
hope you can  soleve..

---

### Post by Caveira2099 on 2009-02-10
Hi all,

I had to write this final post about Linux on acer 4530. Comparing all distros I have tried, OpenSUSE 11.1 final is the best. Simply everything works out of the box, even on 32 or 64 bit: sound wheel, keyboard (multimedia keys!!), webcam, wireless card...

One other great advantage: NVidia official repository = automatically updated official drivers = fully 2d and 3d support.

I am using 64 bit OpenSUSE 11.1 for my productive work. No single problem so far.

Those who still face problems should go for it.

Cheers,

---

### Post by cmc1786 on 2009-03-04
I just had to create and account to tell you all specifically how thankful I am of this post. I have spent about 3 months reading up different things to try and have gone through about 20 dvd's of different versions just trying to find something to work. I was about a week away of trading my computer in for something I knew would work a lot easier. I do not know how I never came across this article till now but this truly has made my day. Thank you so much. Sadly bought quite a few books about linux and network security to try and learn a good bit for school but could not go anywhere with the fact could not even get linux on my computer. Download openSUSE that you recommended as we speak. Like I said I can not even tell ya thank you enough for how helpful this post is.

---

### Post by russell5 on 2009-03-10
I am currently running 9.04 alpha 64bit on this laptop. Everything worked right out of the box. The hardware drivers even install Nvidia 180 for me and there is both 2d and 3d. I am assuming when the final release comes out it will be the same(i hope).

---

### Post by LashSilence83 on 2009-03-10
Debian 5 runs quite smoothly on this system as well...

---

### Post by Caveira2099 on 2009-03-11
Hi all, it's been some time I don't post here, probably because my problems are long gone too... :P

It's always good to know which distros have updated the initrc scripts so that the hardware of this notebook is correctly detected, not resulting in kernel panics....

I am quite happy with OpenSUSE, and I don't plan to switch back to Ubuntu because of the easiness of rpm native support (LSB) gives me. I use some industry software that require lots of symlinking and other tweaks when running in Debian-based distros.

But I'm glad to know Ubuntu 9.04 and Debian 5 are ok with the laptop. I'll send this info to other coleagues who also bought one.

@cmc1786 : Thanks for your reply! Good knowing this post is fullfilling its purpose!

Cheers,

---

### Post by nikolaiortiz on 2009-03-11
Hi @LashSilence83.
did Debian 5 work well out of the box?

@Caveira2099 i tried opensuse and the wireless didn't work.
and the sound using flash didn't work too..

i got a acer 4530 the athlon x2 version.

my ubuntu 8.10 32 bits works fine out of the box except the flash sound but i follow some instruction and all work fine now.

@russell5, did all work fine even the sound?

XD

hails.
N.

---

### Post by russell5 on 2009-03-11
The audio worked almost perfectly out of the box. The sound coming out of the speakers worked no problem and so did the volume control. The one thing that didnt work is when you plugged in headphones to the headphones jack sound would not come through them and continue to come out of the speakers. I fixed this by adding this line to "/etc/alsa-base.conf"
"options snd-hda-intel model=auto"

---

### Post by Caveira2099 on 2009-03-12
Hi [nikolaiortiz]("http://ubuntuforums.org/member.php?u=191413"), everything worked perfectly out of the box for me with OpenSUSE, just like russell5 just said. My notebook model is 4530 with athlon x2 too.

---

### Post by nikolaiortiz on 2009-03-12
i dont know what happend then... i try opensuse and the wireless dint work, the audio didn't work, :P

---

### Post by nerd0795 on 2009-03-15
I would like to install linux on the exact same laptop.  The Anthlon X2, though mine doesn't have a fingerprint reader or webcam.  

I ended up trying an Ubuntu 8.10 install with Wubi instead of a full install, with partitioning.  Ended up it was buggy, and slow so I uninstalled it.  

1) Do you end up getting a high pitched beep on a random restart.  I tried installing Ubuntu on wubi and on my 15th reboot, I got a loud pitched beep.

2) Why 64 bit not 32 with opensuse.

3) Does the wireless work?

4) Is the performance good on the laptop?

Thanks in advance :D

---

### Post by afm93 on 2009-03-29
> **Caveira2099 said:**
> 
But I'm glad to know Ubuntu 9.04 and Debian 5 are ok with the laptop. I'll send this info to other coleagues who also bought one.


I'll have to install Ubuntu 9.04 then when it's released, Vista's giving me some headaches.

---

### Post by nikolaiortiz on 2009-03-29
@Caveira2099 Are you using opensuse 64?
is really Ubuntu 9.04 working well out of the box,the quick buttons too?
or have to do some tricks ;)?

I'm using 8.10 with fluxbox and get a better performance and also i had do this to get audio for flash pages: 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by LashSilence83 on 2009-03-29
Just wanted to give another update on this laptop... I have gone on to install both debian 5 and pclinuxos 2009 and both worth quite well (for the most part). Here is where I currently am with the two: 

pclos - (out of the box) wireless, graphics, vga out, sd card, flash, etc. 
however, the sound stutters and is unbearably static-y, and the webcam has yet to work properly, even after uvcvideo and /dev permission tricks, also volume roller and audio outputs don't work. 

debian5 - install went very smoothly(new gui installer is nice), nvidia 180.29 drivers were installed without incident, wireless with ndiswrapper, sd cards recognized, vga out, volume roller works
What doesn't work at all in Lenny is sound, audio outputs, and the webcam. (I have tried to look for solutions, but none have helped.)


That's the news so far...

---

### Post by nikolaiortiz on 2009-03-30
Well, all so fine on Ubuntu 8.10...
But CPUfreq is not available, also the Temperature Sensors. :(

Any ideas?

---

### Post by aravind_svu on 2009-04-01
> **russell5 said:**
> The audio worked almost perfectly out of the box. The sound coming out of the speakers worked no problem and so did the volume control. The one thing that didnt work is when you plugged in headphones to the headphones jack sound would not come through them and continue to come out of the speakers. I fixed this by adding this line to "/etc/alsa-base.conf"
"options snd-hda-intel model=auto"

Dude Russel5,
         You are a genious man. I had been struggling to get this work on my laptop(ACER ASPIRE 4530). By just adding your line, to alsa-base.conf, It just worked. Although, for Jaunty Jackalope Ubuntu 9.04, this file is not in /etc/ but in /etc/modprob.d/.

Finally I can watch porn, without arousing my roommates :lolflag:


I couldnt get my webcam work on linux though, It didnt work in Windows VISTA either. It works on its own time.. I thought its a driver problem, but now I feel its a hardware problem.. Anyway I am not the one making porn.. I just watch them so I wouldnt worry much :lolflag:

---

### Post by LashSilence83 on 2009-04-02
I'm beginning to wonder how we are all getting these mixed results when we all own the exact same laptop... It's just strange.

---

### Post by nikolaiortiz on 2009-04-03
> **LashSilence83 said:**
> I'm beginning to wonder how we are all getting these mixed results when we all own the exact same laptop... It's just strange.

me too

---

### Post by russell5 on 2009-04-03
Well i think its funny that mine has a button on the left for bluetooth but mine does not have bluetooth. I think thats a good indication that they are all different in some way.

---

### Post by nikolaiortiz on 2009-04-04
yep.. i see that too..russell5
my laptop is a acer aspire 4530 Geforce 9100M G AMD athlon X2 64
no bluetooth., wireless atheros.
AR928X Wireless Network

:)

---

### Post by 3rag0n on 2009-04-08
well. i have the bluetoth button and bluetooth works welll.. :S

and btw,... u r right aravind... the webcam seems faulty.... both in vindo wista and intrepid... sometimes it works, sometimes it doesnt...

---

### Post by tmarthal on 2009-04-15
> **nikolaiortiz said:**
> is really Ubuntu 9.04 working well out of the box,the quick buttons too?
or have to do some tricks ;)?

I'm using 8.10 with fluxbox and get a better performance and also i had do this to get audio for flash pages: 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I just installed Ubuntu 9.04 from AMD64 alternative beta disk (note that whenever you can't get something to boot with a liveCD, try the alternate CD... that's what they are for) and everything works great. I had to install the non-free nvidia binary driver. The system started with the vesa driver (I believe), and after updating and upgrading the nvidia non-free binary driver was avaliable from the 'System->Administration->Hardware Drivers'. Sound from speakers works good. 

Everything seems to be working. Flash sound is fine on youtube (with the flashplugin-nonfree package). 

I had a problem with the 'Problem with Audio Playback in Skype', as in the troubleshooting area here: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) .. I had to set the default sound device within Skype to 'Pulse'. Webcam works 100% (Acer Crystal Eye webcam). 

Note that there might still be issues with the suspend, but I believe that the developers will work that out when 9.04 is 'released' out of beta.

---

### Post by nikolaiortiz on 2009-04-21
Hi..all
i been fighting a lot .. 
now i got a fast Ubuntu 8.10  with fluxbox 
Nvidia 180.41 linux kernel 2.6.29.1 
amost work fine but ..
the sensors thing still fail
~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +70.0°C  (crit = +105.0°C) 

the cpufreq management broken.
Umm before i compile the kernel the wireless LED didn't work, after compile work!!!
before i have a annoying message on dmesg "ForceXPAon 0" all the time..
now after compile the message disappear..

:)
please for those who install ubuntu 9 tell me if your headphones works and if the sensors works better :)


pd: Sorry my french ;)

---

### Post by nikolaiortiz on 2009-04-22
OK.. 
again ..
finally could make the powersaved thing.. 
looking the dmesg thing i see that powersaved was loading a incorrect module he was loading  speedstep-centrino.ko, so i make this..
2.6.29.1.20090421 is my compile kernel maybe you should look for 2.6.27-11-generic/ 2.6.27-7-generic/ or some like that

```

sudo su
cd /lib/modules/2.6.29.1.20090421/kernel/arch/x86/kernel/cpu/cpufreq/
mv speedstep-centrino.ko speedstep-centrino.ko.back
ln -s powernow-k8.ko speedstep-centrino.ko

```

maybe have to be a better way to do it but  i newbe  :P
umm after compile the kernel i saw a really bad thing 
i lost my tty's
if some one can help me please :(

---

### Post by nikolaiortiz on 2009-05-02
Hi...
well maybe i had to follow the old line  "if it isn't broken, don't fix it"

I fight against my problems, the ttys thing and finally work.
but still i have that annoying problem about keyboard i cant make this 
```

á

```
the only thing that i get is this 
```

'a

```
so i migrate to 9.04 .. 
men the problem didnt fix and what is worst...
the power saved don't work again.
for more bad things i have problems with octave.
this is a storm of  bad things...
any suggest please?

---


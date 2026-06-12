---
title: "nvidia 177.80 driver problem"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2008-10-10
hello all.

im currently running the beta of intrepid (kubuntu 64bit) and im having an issue with the new nvidia driver, that being on my system it doesnt work (i have an nvidia 8600gt pci express card)

i have tried to install the driver and activate it (by going to hardware drivers in the system menu) but nothing happens, if i run nvidia-settings from a terminal i get a message saying that im not using the nvidia x driver and that i should run nvidia-xconfig as root, if i do this then when i restart x all i get is a black screen with white letters saying checking battery state.

any ideas ?

---

### Post by punong_bisyonaryo on 2008-10-10
Edit: whoops, replied too soon. Hmmm, any messages? What happens after checking battery state? And was your video card working in Hardy?

---

### Post by philinux on 2008-10-10
> **techno-mole said:**
> hello all.

im currently running the beta of intrepid (kubuntu 64bit) and im having an issue with the new nvidia driver, that being on my system it doesnt work (i have an nvidia 8600gt pci express card)

i have tried to install the driver and activate it (by going to hardware drivers in the system menu) but nothing happens, if i run nvidia-settings from a terminal i get a message saying that im not using the nvidia x driver and that i should run nvidia-xconfig as root, if i do this then when i restart x all i get is a black screen with white letters saying checking battery state.

any ideas ?

You're posting in the wrong forum. Click the Report button and ask the mods to move the thread to here.[ Ibex]("http://ubuntuforums.org/forumdisplay.php?f=346")  You'll then get the help you need. I hope this isn't your main machine.

---

### Post by techno-mole on 2008-10-10
my bad, i will see about getting it moved.

the driver works with the earlier kernel ( which is what im using at the moment)

so just to clarify the 177.80 nvidia driver (well for me anyway) doesnt want to work on the 2.6.27-6-generic kernel, i cant activate it or do anything with it.

but im currently running the 2.6.27-5-generic kernel and the driver is working fine, no problems that i can see.

---

### Post by Rocket2DMn on 2008-10-10
Moved to Intrepid Ibex Testing and Discussion.

---

### Post by klamari on 2008-10-10
Hi there,

I am working on a similar problem for 2 days now, tried whatever I could find on Google and still the battery is checked on my desktop.
Hope someone has a solution...

Using
- 8.10 AMD64
- All updates/upgrades installed (kernel 2.6.27-6-generic)
- Graphic Card is Nvidia Geforce 7600GS/6100
- Acer Aspire E380

Using 2.6.27.4 machine tried first time running to use 177.80 but gives a message about an unsupported WMI interface, now it goes to the console login.
With 2.6.27-6 still checking battery, maybe I should install one?:)

Everything works fine with Hardy.

Thanks in advance

martin

---

### Post by craigyjack on 2008-10-10
Yeah, the new nvidia drivers are broken and messed up in 8.10 right now. I went to install the Beta, and on my system I never got anything other than a horrible mob of flashing colorful lines as my display (its totally corrupted).

I would suggest if you have nvidia to not use 8.10 right now and wait until release. I tried several things and finally reinstalled back to 8.04.

I have filed a bug on the new nvidia driver, and I hope it is getting worked on. The new drivers and stuff are weird in 8.10 because of jockey and the non-use of xorg.conf much in 8.10, so I understand some issues getting the proprietary drivers working well with the new system. My system didnt work with the old kernel or the new one, and I couldn't even get it to use the vesa driver or something other than nvidia to work.

I am just having some patience and hoping nvidia stuff all works well when 8.10 is released final at the end of the month. :)

---

### Post by techno-mole on 2008-10-10
its curious, could it be that it is not just the drivers, but a combination of the driver not working correctly with the latest kernel ?

the reason i ask is because if the driver is corrupted or broken or what ever, then why does it work on the older kernels, in my case im currently running 2.6.27-4-generic (at least i think it is) and the 177.80 nvidia driver and its running fine ? it just wont work with the later kernel - 2.6.27-6-generic

strange.

---

### Post by klamari on 2008-10-10
Hi techno-mole

I tried the 173 driver as well with 8.10, not working, wants to check my battery...:)
In fact, it does not really hang up on doing this but will not load the graphical mode, guess the driver is not so much the issue then as 173 is doing fine on Hardy.
The nv driver works, but I would want to have some 3d as well

Greetings 

martin

---

### Post by Odisej on 2008-10-10
Ok, I don't know if this will solve your problem but it did mine. I did an update/upgrade after which I could not enable nvidia driver v177. After restart it would go into one of those "rescue modes". After which only oss driver would work but I was unable to activate nvidia's driver. 

It worked only after I copied the original xorg.conf (the one I was using was slightly altered), selecting 173 driver, restarting and installing 177 again. After restart everything worked. 

Did you try something like this? The battery checking is something I did not encounter but I'm not using laptop.

Regards,

Odisej

---

### Post by klamari on 2008-10-10
Hi odisej

I guess you mean the original "empty" xorg.conf?

Did I mess things up with doing nvidia.install and thereby altering the original file?

Just asking to learn, maybe 8.10 uses different approaches than what I was used to....

If answer to 1. is yes I will try

b.t.w.: I am using a desktop, still the battery is checked...????

Greetings

martin

---

### Post by sjhstorm on 2008-10-10
It may be that if you tried selecting the driver through "jokey" that it has written to xorg.conf but has not completed properly due to the nvidia headers missing (I had this problem).

If you boot into recovery mode and at the menue select fix x, this will back up xorg.conf and hopefully produce a working x , all be it with just the nv drivers.

If all goes well and you have your desktop back, open your package manager Adept or synaptic and search nvidia. You can then select and install the required drivers / headers (in this case the nvidia-177. Once installed go back to jockey and select driver and this time all should work.

---

### Post by ronacc on 2008-10-10
try this, reinstall linux-image-generic , that will trigger dkms to recompile the driver for the -6 kernel , if you are running the -4 kernel without recompiling the driver it is wrong for the -6 kernel, if the 177.80 driver was updated after the linux-image was installed then it would not have been compiled for it .

---

### Post by techno-mole on 2008-10-10
i did mess around with various xorg configurations, i did get it to work a couple of times, that is 8.10 + nvidia 177 + 2.6.27-6-generic, but every time i rebooted the system it kind of reverted back to the issue i was having, so for now (well at least until the end of the month) im back on 8.04 (running kde4.1)

i think i'll wait until they release the rc.

the battery checking thing was and still is a bit of a puzzle, especially when you consider that im not using a laptop, im running kubuntu on a desktop system that i built myself - 
amd athalon x2 5200 (dual core)
ecs nvidia geforce main board.
nvidia 8600gt pci express graphics card
2 gb of ddr2 ram @ 800mhz
sound blaster audigy sound card.
plus 2 sata drives (1 x 80gb and 1 x 500gb)
not the best, but it does the job

---

### Post by plun on 2008-10-10
> **ronacc said:**
> try this, reinstall linux-image-generic , that will trigger dkms to recompile the driver for the -6 kernel , if you are running the -4 kernel without recompiling the driver it is wrong for the -6 kernel, if the 177.80 driver was updated after the linux-image was installed then it would not have been compiled for it .

@ronacc

I think its better to move on to kernel 2.6.27-7.

Cant you see it within US repos ?   I have had this kernel at least 2 hours.

---

### Post by klamari on 2008-10-10
sjhstorm:
thanks for the advice, tried and did not work....

plun: 
will lookout for version 7 driver... (just saw your posting)

looks like other people are still working on the same problem

greetings

martin

P.S.: just for the fun of it I just installed 8.10 on my notebook with no Nvidia on it, the same issue, "checking battery  <OK> on the screen and nothing else, installed it with the new driver after apt-get upgrade and apt-get dist.upgrade, 

well, I am puzzled

---

### Post by ronacc on 2008-10-10
@plun I'm checking now , I hadn't done my evening update yet , I usually update at  around 0700 , 1700 & 2300 local . yes it's there but "held back" 44 megs of other updates though , after they finish installing I'll see why -7 is held back for me.

---

### Post by ronacc on 2008-10-10
the treat recomends as dependencies thing was what was holding back -7 , it's up and running now :)

---

### Post by plun on 2008-10-10
> **ronacc said:**
> the treat recomends as dependencies thing was what was holding back -7 , it's up and running now :)

Ok...  I am using startupmanager and turned on text during startup.

I noticed a **new DKMS service start, **cannot remember that I´ve seen it before.  I terrible broke my own nvidia driver install yesterday and must "poison" my PC to get the driver back. (the old tty way)

Now it seems to be Ok again with latest kernel.

---

### Post by ronacc on 2008-10-10
DKMS has been working ok me as long as things update in the "correct" order , as I posted above if the kernel updates before the driver I have to reinstall the image to get dkms to see the new driver.

---

### Post by dabl on 2008-10-10
177.80 is working great and looking good here.

```
dabl@ibex:~$ uname -a
Linux ibex 2.6.27-7-generic #1 SMP Fri Oct 10 03:55:01 UTC 2008 x86_64 GNU/Linux
```

[[IMG]http://img353.imageshack.us/img353/1363/nvidia177sq8.th.png[/IMG]](http://img353.imageshack.us/my.php?image=nvidia177sq8.png)

[[IMG]http://img291.imageshack.us/img291/1239/k8mx2.th.png[/IMG]](http://img291.imageshack.us/my.php?image=k8mx2.png)

---

### Post by plun on 2008-10-10
> **ronacc said:**
> DKMS has been working ok me as long as things update in the "correct" order , as I posted above if the kernel updates before the driver I have to reinstall the image to get dkms to see the new driver.

Yes... but now I can see this DKMS check also during boot.
I cannot remember that I´ve seen it before.

I am rather sure that this check was missing before and caused that a driver didnt load.   

(With Startupmanager you can use your splash and also enable boot sequense/startup messages, OK/Fail for all services)

---

### Post by ronacc on 2008-10-10
I hate to admit it but I don't pay any attention to the boot messages unless I have a problem !

---

### Post by dabl on 2008-10-10
> **ronacc said:**
> I hate to admit it but I don't pay any attention to the boot messages unless I have a problem !

Me neither.

Not only is the plot boring, there's no pictures!

:lolflag:

---

### Post by hajk on 2008-10-11
Nvidia 177.80 + 2.6.27-7 kernel: runs fine on computer with GeForce 8400GS graphics card; but fails on other computer with GeForce 8600GT... Fortunately, there's still a few weeks development left...

---

### Post by mosimea on 2008-10-11
I have a two machines, one with a 7600 and another with a 9600GT working perfectly with the 177.80 driver.  Both machines use the 2.6.27-7-generic kernel.  

Did you manually install the driver or did you use the restricted drivers applet to install it? 

On Hardy I was in the habit of downloading and manually installing the latest drivers from Nvidia, but with the upgrade to Intrepid I went the applet route with much success.

---

### Post by hajk on 2008-10-11
Used the DKMS-way (?) in both cases, only difference: the computer with the 8600GT graphics (where 177-8- fails) runs Intrepid upgraded since early September; the one with 8400GS graphics (177-80 OK) was installed yesterday from the Beta release and upgraded from that. I could try and reinstall the 2.6.27-7 kernel, like someone here suggested, since I still have the -6 kernel as well.

---

### Post by hajk on 2008-10-11
> **hajk said:**
> ... I could try and reinstall the 2.6.27-7 kernel, like someone here suggested, since I still have the -6 kernel as well.
Well, that worked (reinstalling the -7 kernel and also reinstalling the 177-80 nvidia-kernel-source package. But I still don't know *why* this solved the problem.

---

### Post by plun on 2008-10-11
> **hajk said:**
> Well, that worked (reinstalling the -7 kernel and also reinstalling the 177-80 nvidia-kernel-source package. But I still don't know *why* this solved the problem.

Then we are 2 which doesnt understand this...:)

Nevertheless its changed now during startup.

Jockey is also a beta version so hopefully it will be perfect.

---

### Post by vgrisham on 2008-10-11
I was able to install 177, but it was not without experiencing an intense pucker factor. Upon restarting, Ubuntu booted into low graphics mode and then froze after forcing me to choose a new "generic configuration for this device". I thought it was toast. After a hard boot, it came up and worked fine with 177 enabled.

One note: I was never able to get the hardware drivers applet to activate the driver; I had to go through synaptic.

---

### Post by Nysomin on 2008-10-11
Until my keyboard and mouse stopped working I had 2.6.27-7 and 177.80 working with my two 8600GTS cards.  I used nvidia's installer for 177.80 and then had to use a live cd(I find it easier this way) to edit my xorg.conf to manually add the busid of my primary card and activate SLi(no longer in nvidia-setting for some reason).  I was able to run Blender 2.47 and Regnum Online just fine.

---


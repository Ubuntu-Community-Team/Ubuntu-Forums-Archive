---
title: "Nvidia Driver Lag Issues"
date: 2009-06-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2009-06-15
Hey:

Don't know if this has been reported.  I tested Ubuntu Karmic Alpha 2 with nvidia driver 180 and normal effects and got extremely laggy performance along with reduced functionality on clicking icons and the like.  On Kubuntu, something similar happens with composite effects and the like being disabled after I enable them...anyone else getting same issues on their side?

---

### Post by zoff_ita on 2009-06-15
Actually I'm running Ubuntu Karmic x86_64 on my laptop with NVIDIA 7600 an I have no problems with kernel 2.6.30-9.

Graphics and effects are fluids...

Bye

---

### Post by PRGUY85 on 2009-06-15
Hmm...Im using the 32 bit version with Nvidia 180, what I always use for Ubuntu lately.  My graphics card is an Nvidia 5700Go (or similar).

---

### Post by xebian on 2009-06-15
> **PRGUY85 said:**
> Hmm...Im using the 32 bit version with Nvidia 180, what I always use for Ubuntu lately.  My graphics card is an Nvidia 5700Go (or similar).

NV 180.xxx is only for 6xxx series and up gpu.  You should be using the legacy 173.xxx drivers

---

### Post by PRGUY85 on 2009-06-15
> **xebian said:**
> NV 180.xxx is only for 6xxx series and up gpu.  You should be using the legacy 173.xxx drivers

Let me check my specs then.

---

### Post by PRGUY85 on 2009-06-15
No, I have the Nvidia Go 7400 sorry.

---

### Post by zenarcher on 2009-06-15
No lag here with an Nvidia 8400GS and the Nvidia 180 driver.

Cheers,
zenarcher

---

### Post by PRGUY85 on 2009-06-15
> **zenarcher said:**
> No lag here with an Nvidia 8400GS and the Nvidia 180 driver.

Cheers,
zenarcher

Any ideas then for my case?

---

### Post by PRGUY85 on 2009-06-15
Update:

Now it doesn't allow me to set desktop effects with driver installed.  The screen flickers for a while and then says Desktop effecs cannot be enabled.

---

### Post by dagrump on 2009-06-16
Just a SWAG as opposed to A WAG, this is a laptop? It would be easier to address your issues with an idea of the equipments spec's. I have no lag issue but I'm using a desktop machine, laptops are a different ball of wax, they require more attention to detail.
So, some spec's might get a few more bites.

---

### Post by PRGUY85 on 2009-06-16
> **dagrump said:**
> Just a SWAG as opposed to A WAG, this is a laptop? It would be easier to address your issues with an idea of the equipments spec's. I have no lag issue but I'm using a desktop machine, laptops are a different ball of wax, they require more attention to detail.
So, some spec's might get a few more bites.

This is a laptop, a Dell XPS M1210 laptop with Nvidia Go 7400 graphics driver. I have never had any issues with Hardware Drivers functionality on Ubuntu (I know this is Alpha, I want to help with bugs)

---

### Post by PRGUY85 on 2009-07-23
I just installed Karmic Alpha 3 on my laptop and this is still happening.  Again, it didn't happen on 9.04.  This is keeping me from using Gnome-Do's Docky!!!

---

### Post by PRGUY85 on 2009-07-24
Has anyone encountered this yet on my laptop/video card?

---

### Post by flavouride on 2009-07-24
Have you even enabled your NV180 proprietory driver at the Hardware menu??

---

### Post by pelle.k on 2009-07-24
> I just installed Karmic Alpha 3 on my laptop and this is still happening. Again, it didn't happen on 9.04. This is keeping me from using Gnome-Do's Docky!!!
No it doesn't! This wont help you with your problem regarding the nvidia driver or compiz, but you may run the gnome compositor using any driver. And thus gnome-do's docky.
In gconf-editor, activate **/apps/metacity/general/compositing_manager**
You **HAVE** to deactivate it before you try enabling effects againg though, just remeber that.

---

### Post by PRGUY85 on 2009-07-24
> **flavouride said:**
> Have you even enabled your NV180 proprietory driver at the Hardware menu??

Of course I enabled them...

Again why is this happening still on Alpha 3 while 9.04 or any previous version has done this is something I want to get to the bottom off.  Is it because a change in driver or kernel?

---

### Post by Otaconda on 2009-07-24
I'm experiencing it, found a bug in LP which I added some log info to:

[https://bugs.launchpad.net/ubuntu/+bug/391461](https://bugs.launchpad.net/ubuntu/+bug/391461)

Starting X with the binary driver loaded performs fine, as soon as you start compiz the draw performance is dire, and you have to kill it to get performance back. 

My card is identified the same as yours:

sudo lshw -class display
  *-display
       description: VGA compatible controller
       product: G72M [GeForce Go 7400]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

Do you have a lot of these in ~/.xsession-errors ?
```
Window manager warning: Failed to read saved session file /home/xxx/.config/metacity/sessions/107b7f1334bc621589124834107010651000000030620023.ms: Failed to open file '/home/xxx/.config/metacity/sessions/107b7f1334bc621589124834107010651000000030620023.ms': No such file or directory
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
```

---

### Post by PRGUY85 on 2009-07-24
Yes Otaconda same story here.

---

### Post by Otaconda on 2009-07-24
No idea what's going on unfortunately :( Would you mind adding your logs to the bug so the devs can compare? :)

Think that bug should probably go against nvidia rather than compiz now.

---

### Post by PRGUY85 on 2009-08-22
Any new developments on this issue? It is still happening with latest updates and Nvidia driver 185.

---

### Post by PRGUY85 on 2009-09-17
This issue has not yet been resolved for Alpha6 .

---

### Post by Diggs808 on 2009-09-18
I am getting the same issue as well.  

I can enable desktop effects, but it is REALLY slow.  Which is unusual since my video card is a 256 mb NVidia GE Force Go 7300.  Every other version of Ubuntu it has worked perfectly out of the box for compiz and everything.  

Any suggestions?  Here is the output of what happens when I run compiz --replace:

diggs@Phoenix:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
diggs@Phoenix:~$

---

### Post by Funnnny on 2009-09-18
> Checking for Xgl: not present. 
Do you install the driver correctly ?
Maybe you have to reinstall it

---

### Post by Diggs808 on 2009-09-18
> **Funnnny said:**
> Do you install the driver correctly ?
Maybe you have to reinstall it 

I think so, since I used the restricted drivers menu to do so.  I can get compositing in Metacity to work just fine, however there is a lot missing when I cannot use my desktop cube....

---

### Post by Funnnny on 2009-09-18
Try to manual install nvidia driver from the nvidia website
first uninstall all nvidia package, and then install it with the official driver

---

### Post by Asraniel on 2009-09-18
> **Funnnny said:**
> Do you install the driver correctly ?
Maybe you have to reinstall it

Xgl was an old replacement for x.org, so this is normal that it is not found.

---


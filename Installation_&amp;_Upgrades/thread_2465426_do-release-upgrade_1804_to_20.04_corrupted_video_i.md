---
title: "do-release-upgrade 18/04 to 20.04 corrupted video issue"
date: 2021-08-01
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2021-08-01
I ran a do-release-upgrade on an 18.04 computer. It ran and produced no errors. However upon rebooting I get a corrupted image on the monitor after logging in. It worked just fine in 18.04. 

```
#  lshw -c video
  *-display
       description: VGA compatible controller
       product: C61 [GeForce 7025 / nForce 630a]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:23 memory:ee000000-eeffffff memory:d0000000-dfffffff memory:ed000000-edffffff memory:c0000-dffff
```

---

### Post by GhX6GZMB on 2021-08-01
Which (x)Ubuntu? My crystal ball is broken.

---

### Post by MAFoElffen on 2021-08-01
Your NVidia Geforce 7025 is using the opensource Nouveau driver... which covers that GPU... You also have 3rd Party, Proprietary drivers available. 

What do you mean, when you are saying that it is now getting a corrupted image? Could you descript that, upload a screenshot or a picture of as an attachment?

---

### Post by rsteinmetz70112 on 2021-08-01
I am using Ubuntu 20.04 
The [screen shot]("http://hamlet.steinmetznet.com/steinmetznet/Screenshot%20from%202021-08-01%2014-23-49.png") doesn't give the full effect because it changes as the mouse moves over the screen.

I thought the Nvidia proprietary drivers for the chipset had been discontinued.

---

### Post by MAFoElffen on 2021-08-01
NVidia Driver 304 supports that card (probably one of the last that did. 

The easiest way, in a terminal session:
```
sudo apt install -y ubuntu-drivers-common
ubuntu-drivers list

```
Inside of the ubuntu-drivers package is a utility called nvidia=detecter which in that last command, it uses this utility to query your GPU, then devides if there is an appropriate driver in the 3rd Party Repo's. If it comes up with matches, it will list those driver package names... So please post the output of that last command...

If it does come up with package names, then do
```
sudo ubuntu-drivers autoinstall
```
It will then pick out the best choice of those drivers and install it.

OR_ You could decide to install one of the packages listed via APT.
```
sudo apt install <package_name>
```
IF there is no drivers listed, tell me, as I know that the package for NVidia Driver 304 is still in the Ubuntu Drivers Team PPA.

---

### Post by rsteinmetz70112 on 2021-08-01
```
# ubuntu-drivers install
No drivers found for installation.
```

I understand that the Nvidia 304 driver is not compatible with current kernels. 
I don't understand why the nouveau driver worked with 18.04 but not 20.04

I looked at this ppa, [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) and it doesn't appear to have a version of the 304 for 20.04 - it looks like the last version is for 18.04

---

### Post by MAFoElffen on 2021-08-01
In that case... The NVidia Driver Version 304 is in the Ubuntu Drivers Team PPA...
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install -y nvidia-graphics-drivers-304

```

---

### Post by guiverc on 2021-08-01
You didn't say which kernel option you were using when using *bionic* or 18.04.  If it was the GA kernel (4.15), then you'd notice a big change when upgrading to *focal*, however may have noticed no change if you were using HWE on *bionic* (18.04; 5.4) and upgraded to *focal* (20.04; 5.4) using GA.

This reminds me of a recent bug report [*reply *]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1930945/comments/5")from Daniel Van Vugt (*vanvugt*) on QA-testing issues on *impish* where my old *nvidia* card has bugs in *nouveau* that are unlikely to be fixed (impacting GNOME & KDE), where the suggestion was to return the box to *focal* or 20.04 & use the older GA kernel. If you're using an HWE kernel; I'd suggest trying the GA kernel.

My other thought - I have no graphic issues at all on that box I'm referring to with other desktops, ie. I'm involved with the Lubuntu team so the box is mostly used for Lubuntu testing and I don't recall every having a video glitch with that Lubuntu (nor with Xubuntu; only Kubuntu & Ubuntu (GNOME) have issues that I recall).  ie. if you're not *tied* to GNOME/KDE, switching to another DE may also be an option.

Note:  I'm no expert with graphics - I ignore it unless it's a problem

---

### Post by MAFoElffen on 2021-08-02
Well a way to check would be for him to do 
```
uname -r
```
...and see if it is HWE or Generic... Now you have me curious about that.

---

### Post by rsteinmetz70112 on 2021-08-02
As I thought after adding the ppa, no drivers were found
```
# apt install nvidia-graphics-drivers-304
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package nvidia-graphics-drivers-304
```
I am using the generic kernel, not the HWE
```
# uname -r
5.4.0-80-generic
```

---

### Post by rsteinmetz70112 on 2021-08-02
As a result of the computer being upgraded successively I've got a number of graphic choices. I'm wondering it this is tied to a specific dm.

I've checked further and lightdm is listed as the default the display manager, gdm3 seems to be active. Not sure how to change to lightdm to check it out.

---

### Post by rsteinmetz70112 on 2021-08-02
OK I guess some progress. The greeter is very messed up and nearly unreadable. but I can actually login.
When I select a user I have several display options those are :
[LIST]GNOME
[*]GNOME CLASSIS
[*]GNOME Flashback (Metacity)*
[*]GNOME Flashback (Compiz)*
[*]GNOME on Xorg
[*]Ubuntu
[*]Ubuntu on Wayland
[*]Unity*
[/LIST]
* These seem to work ok.

---

### Post by MAFoElffen on 2021-08-03
Did you select any of those video choices? Did you got to the Software & Updates App, and make sure the 3rd Party Repo is selected, and good to the Alternate Drivers Tab to see what it shows for choices of appropriate drivers? What driver are you using right now?

---

### Post by linerman on 2021-08-04
I had same problem lately but with different nVidia card.
It happened during upgrading driver. I guess there was some conflict with Nouveau and nVidia drivers. 
I fix that with installing Nouveau driver, that purged all of the nvidia files. 
Next step was installing proper Nvidia card through Alternate Drivers Tab.

---

### Post by rsteinmetz70112 on 2021-08-04
> **MAFoElffen said:**
> Did you select any of those video choices?

I tried all of them. I noted that ones that sort of work. The greeter is still messed up.

>  Did you got to the Software & Updates App, and make sure the 3rd Party Repo is selected,

I added the PPa as you suggested.  The appropriate proprietary driver is the nvidia-304 which is not available for 20.04

> and go to the Alternate Drivers Tab to see what it shows for choices of appropriate drivers?

ubuntu-drivers identifies no other drivers pertty sure the app will show the same..

>  What driver are you using right now?

nouveau

---

### Post by MAFoElffen on 2021-08-04
> **rsteinmetz70112 said:**
> >  	 		 			 			 				 Did you got to the Software & Updates App, and make sure the 3rd Party Repo is selected, 			 		

 	
 
I added the PPa as you suggested.  The appropriate proprietary driver is the nvidia-304 which is not available for 20.04
Software and Updates app, in the first Tab (Ubuntu)... Where it says Propriatary Drivers For Devices (Restricted)... Please confirm that the checkbox is selected...

---

### Post by MAFoElffen on 2021-08-04
I just checked with NVidia and parsed through their support matrix for legacy drivers 
 - [https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/) (Ver390 does not, ver340 does)
and cross-reference fro what I see in Ubuntu for 20.04 repo's... Version 340 does support your card.
```
sudo apt install nividia-340
```
Not sure why that does not show under Additional Drivers... Maybe that is something to report to Launchpad as a Bug(?)

---

### Post by rsteinmetz70112 on 2021-08-05
Not sure it matters but I don't have a card - it's the motherboard graphics chip.
Are your sure nividia-340 supports the GeForce 7025 / nForce 630a?I can't find any corroboration.
I'll try it as soon as I can get to a 20.04 computer or one I can try to upgrade, it will be a few days.

---

### Post by MAFoElffen on 2021-08-05
The attachments are screenshots from the first link I posted in that last post. You apparently didn't look at it. No matter.

The second attachment shows that it is the NVidia Legacy driver page and the Version 340.xx driver... and in the first attachment, that is further down the page, showing your Onboard GPU... Also shown that the web address is that same page.

So yes, "NVidia says" that version of their driver covers your NVidia GPU. 

That's as much as I can do for you. I have only been supporting XServer for 33 years now, supporting XOrg XServer High End Graphics (AMI/AMD, NVidia, Intel) for 15 years and the Linux Graphics Layer for 12 years. But what does that matter. I'm just here anonymously trying to help people.

The only other thing I can recommend... Is that you are running the current "-Generic" Kernel, instead of the "-HWE" Kernel. One other person told you that "he" is doing better on his similar legacy NVidia GPU, just by using the "-HWE" Kernel.

Note that one person gave you incorrect advice: That person recommended using the "Mainline" Application to change kernel "versions"... But for you and your circumstances, that was bad advice and doesn't fit your specific circumstances. You do not need to change kernel version numbers. You need to try a different kernel "type" of the same version. Mainline Kernels, from the MainLine PPA are just basic Linux Kernels, package there (usually for testing) without the extra tuning of the Kernels that are in the Ubuntu Repo's. They are not the same as the -Generic and -HWE Kernels... 

HWE is not just the Kernel, but a whole Hardware Enablement Stack, that helps with Graphics and other hardware... Not just the Kernel...

Rather than those instructions he gave, you would do
```
sudo apt install --install-recommends linux-generic-hwe-20.04
```
Just doing that may help your video, with just running the opensource Nouveau Driver... (or any other driver)


It's in your hands now. You can make your own decisions. I try to give  you enough information for you to make an informed, educated decision.

Go out... Google and confirm for yourself... Then do what you decide for you.

---


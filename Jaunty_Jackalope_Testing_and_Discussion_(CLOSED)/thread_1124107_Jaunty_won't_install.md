---
title: "Jaunty won't install"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nuclearpidgeon on 2009-04-13
Hi, sorry if this is the wrong place to post this.

I've downloaded the Jaunty beta, and already installed it on my laptop - it's pretty good. I've also managed to hook it into the windows 7 bootloader (I have 3 OSes on my Laptop, the Win7 beta, XP and Jaunty). I tried installing Jaunty on my PC, but every time it finishes scanning the mirror, when it goes into final configuration, the screen goes green with all these jaggy lines, then loads the login screen (this happens on my laptop when you change resolution/projector settings). Because of this, the install never completes. i've tried about 3 times now and each time has failed - it hasn't even installed the bootloader.

Any ideas? Again, sorry if I've come to the wrong place - I know how annoyign it is to get the wrong post in the wrong thread.

---

### Post by Cybie257 on 2009-04-13
Any specs you can give on the PC? 

-Cybie

---

### Post by nuclearpidgeon on 2009-04-13
> **Cybie257 said:**
> Any specs you can give on the PC? 

-Cybie

Intel C2D e6400 @ 2.13GHz (note, I'm installing the 64-bit version of jaunty)
NVIDIA 7600GT (The desktop effects require a downloaded driver, even though it's running off the livecd)
4GB of RAM
GIGABYTE GA-945P-S3 Motherboard

if you need anything else just ask

---

### Post by Cybie257 on 2009-04-13
Hmmm. I'm stumped. All good hardware that should be easily recognized, especially video. 

You say the LiveCD works. What I would do, as I've encountered this in the past, is to re-download, or just re-burn the CD and see if that fixes things as there could be a defect (on the CD) causing something not to install. The LiveCD doesn't always reflect that since some things are not accessed, while installing it accesses just about everything on the CD.

I believe there is also an option to check the CD when it first boots up, which 'should' indicate any problems. But, as cheap as CD's are these days, might be better to just re-burn and try again. 

Otherwise, the only thing in question is possibly the MBR/Boot sector based on the fact that you are running Windows 7... Micro$oft (as with Vista) is trying all they can to not allow you to dual boot Linux. (At least I feel that way, LoL) Not sure of what the changes might be with Windows 7 Bootloader, but possible that the Linux Installers have yet to catch up to the changes. ???

-Cybie

---

### Post by kmnielsen on 2009-04-13
"Hmmm. I'm stumped".....

Well i have been reading this forum for a cpl of weeks and Ubuntu got some REAL big issues on the grafic side. They cant handle digital correctly in 90 % of the time ! So many threads on this subject that one cant be "stumped" about it, only cry and say oki one more got in the trap !

And i guees as the relase date get near its just gonna be an UPSSSSSSS solved solution once again.

Its been a problem since the early days of PowerPC G3 G4, and form 7.10 do to the fact most PC i386 today are sold with grafic-cards with digital output instead of VGA !

What i dont get is WHY Ubuntu dont come clear telling pepl YES WE HAVE A PROBLEM. Think how many pepl installed Ubuntu and they cant use the system ! That could have been prevented in a big headline " WE GOT SOME ISSUES " ( but we are working on it ).... NO NOTHING IS SAID !

IM NOWAY AGAINST LINUX OR UBUNTU... But one gets fustrated when using ALOT of time on trying too intall when a simple "dont install if" could have been made !

---

### Post by nuclearpidgeon on 2009-04-13
> **Cybie257 said:**
> Hmmm. I'm stumped. All good hardware that should be easily recognized, especially video. 

You say the LiveCD works. What I would do, as I've encountered this in the past, is to re-download, or just re-burn the CD and see if that fixes things as there could be a defect (on the CD) causing something not to install. The LiveCD doesn't always reflect that since some things are not accessed, while installing it accesses just about everything on the CD.

I believe there is also an option to check the CD when it first boots up, which 'should' indicate any problems. But, as cheap as CD's are these days, might be better to just re-burn and try again. 

Otherwise, the only thing in question is possibly the MBR/Boot sector based on the fact that you are running Windows 7... Micro$oft (as with Vista) is trying all they can to not allow you to dual boot Linux. (At least I feel that way, LoL) Not sure of what the changes might be with Windows 7 Bootloader, but possible that the Linux Installers have yet to catch up to the changes. ???

-Cybie

There's nothing wrong with the LiveCD - I've already installed a copy of Jaunty off the same CD on my laptop, and I have succsessfully integrated it with both the Windows XP and Windows 7 Beta boot loaders.

Perhaps it's something to do with the graphics driver - maybe when ubuntu configures the hardware, it does something funny and causes a graphical change which triggers a logout, cancelling the install before the bootloader can be installed. (Note: The bootloader problem has nothing to do with Windows - I checked on the linux partition and under /boot there was no grub directory, indicating that grub hadn't been installed)

I'll try installing the official NVIDIA driver through restricted drivers on the LiveCD, see if that fixes anything

---

### Post by Aubergines on 2009-04-13
> **kmnielsen said:**
> Well i have been reading this forum for a cpl of weeks and Ubuntu got some REAL big issues on the grafic side. They cant handle digital correctly in 90 % of the time !
90% is a pretty big number, I'd like to see how you arrived a that figure. In this day and age I'd expect a significant proportion of users do use linux on machines with TFT and DVI. If it really DVI support really was a problem you'd see the forums literally flooded with them. Instead I get 250 hits for the generic string "DVI" (which could be anything) out of 1,005,649 posts.

---

### Post by nuclearpidgeon on 2009-04-13
> **kmnielsen said:**
> "Hmmm. I'm stumped".....

Well i have been reading this forum for a cpl of weeks and Ubuntu got some REAL big issues on the grafic side. They cant handle digital correctly in 90 % of the time ! So many threads on this subject that one cant be "stumped" about it, only cry and say oki one more got in the trap !

And i guees as the relase date get near its just gonna be an UPSSSSSSS solved solution once again.

Its been a problem since the early days of PowerPC G3 G4, and form 7.10 do to the fact most PC i386 today are sold with grafic-cards with digital output instead of VGA !

What i dont get is WHY Ubuntu dont come clear telling pepl YES WE HAVE A PROBLEM. Think how many pepl installed Ubuntu and they cant use the system ! That could have been prevented in a big headline " WE GOT SOME ISSUES " ( but we are working on it ).... NO NOTHING IS SAID !

IM NOWAY AGAINST LINUX OR UBUNTU... But one gets fustrated when using ALOT of time on trying too intall when a simple "dont install if" could have been made !

Just to clarify, I've never had any major issues with Ubuntu and graphics drivers in the past - the only issue I've had is that since either 7.10 or 8.04 I've had to install the official NVIDIA driver for the advanced graphics to work.

You can't blame Ubuntu/Linux for not working on peoples computers - I've run Ubuntu on a range of different machines, and all of them have worked fine. The problems that people encounter are usually introduced when the systems that they are installing Linux onto have... exotic hardware. Usually Windows works fine, because you'll get a driver disk that will make everything work fine, but most of the time there's no Linux driver.

I'm not quite sure whether you realize this or not, but AFAIK there is no proprietary code whatsoever on the Ubuntu CD that you download (correct me if i'm wrong about this). When you run the LiveCD, you are using open drivers which have been hand coded by the community to work on that hardware. Considering the amount of computers that Ubuntu can run on, this is quite an amazing feat, and also because of this way the drivers are made, of course there are going to be errors and the like.

Also, next time you post, could you take a minute to go over what you've written/typed? no offense or anything, but it's just a bit hard to understand what you're trying to say

P.S. what do you mean by 'UPSSSSSSS'?

---

### Post by nuclearpidgeon on 2009-04-13
> **Aubergines said:**
> 90% is a pretty big number, I'd like to see how you arrived a that figure. In this day and age I'd expect a significant proportion of users do use linux on machines with TFT and DVI. If it really DVI support really was a problem you'd see the forums literally flooded with them. Instead I get 250 hits for the generic string "DVI" (which could be anything) out of 1,005,649 posts.

Another note on this - usually DVI/VGA (ie which one to use) is handled by the firmware on the video card, not the driver on the PC. At least until you start to use both ports for dual monitor/projector/TV setups.

Remember what I said about community-maintained drivers before - you've GOT to expect bugs when they're pitching to such a large audience of so many different types of videocards, and what amazes me is how many different cards these drivers support out-of-the-box. Case in point: when running the Jaunty/Intrepid/Hardy LiveCD on my laptop, I can get fancy 3D accelerated graphics without ANY configuration whatsoever. If you also consider that the driver also works with WINE and can play games like Counter-Strike Source through an entire open-source, community maintained system... this is what makes Ubuntu so awesome 8-)

---

### Post by Aubergines on 2009-04-13
> **nuclearpidgeon said:**
> Another note on this - usually DVI/VGA (ie which one to use) is handled by the firmware on the video card, not the driver on the PC. At least until you start to use both ports for dual monitor/projector/TV setups.
Indeed, which is why you do not require any addition software to boot into BIOS regardless of whether which output you're plugged into.

---

### Post by kmnielsen on 2009-04-13
@Aubergines

Instead of seaching for DVI why not try seaching for install issues, nvidia, ati and so on.....

Its still the same problem but whit other seach words ! AND IT IS A PROBLEM, AND NOT A NVIDIA PROBLEM !!!

Nvidia or ATI, runs fine on Opensuse & Debian so telling pepl its a nvidia and ATI problem is just babeling ! Ubuntu got a problem !

---

### Post by Aubergines on 2009-04-13
> **kmnielsen said:**
> @Aubergines

Instead of seaching for DVI why not try seaching for install issues, nvidia, ati and so on.....

Its still the same problem but whit other seach words ! AND IT IS A PROBLEM, AND NOT A NVIDIA PROBLEM !!!

Nvidia or ATI, runs fine on Opensuse & Debian so telling pepl its a nvidia and ATI problem is just babeling ! Ubuntu got a problem !
Because install issues with nvidia, ati and so on has little to do specifically with DVI. You can do the same search on a windows forum and get as many hits. You'll find threads on all sorts of problems on all sorts of hardware, what I'm saying the magnitude of DVI problems isn't anything like as you claim. I'd even go as far as to say it's very rare contrary to your ubuntu `cant handle digital correctly in 90 % of the time`.

*edit: besides this is going a hell of a lot off topic from nuclearpidgeon's orignal post :P*

---

### Post by nuclearpidgeon on 2009-04-13
Hmm. I tried to install the driver through Restricted Drivers, but once it got to the download and install phase, it just hung at 0% for a bit (although it was definitely downloading, I could see the activity port on my LAN card flashing(, and once it was done I just got a blank error message.

More on the problem though, I was submitting a bug report to launchpad when I came across this:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/260001](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/260001)
However this seems to have come from the alphas, not the beta. I'm submitting my results now, and am running the installer again to get a syslog of the crash.

---

### Post by nuclearpidgeon on 2009-04-13
> **kmnielsen said:**
> @Aubergines

Instead of seaching for DVI why not try seaching for install issues, nvidia, ati and so on.....

Its still the same problem but whit other seach words ! AND IT IS A PROBLEM, AND NOT A NVIDIA PROBLEM !!!

Nvidia or ATI, runs fine on Opensuse & Debian so telling pepl its a nvidia and ATI problem is just babeling ! Ubuntu got a problem !

There's nothing wrong with ubuntu that's not experienced with other linux distros too. Liek I said before, I've got an NVIDIA card, and I've managed to get CS:S running FASTER (150fps max instead of 120, althoguh the framerate was very wild, it went from 10 to 150 in a few seconds...) on WINE than on Windows XP.

Also, look at the WineDB - almost 60-70% (i might be wrong here, but [this is pretty good evidence]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=distribution&sTitle=View+Distributions&iItemsPerPage=25&iPage=15&iItemsPerPage=25&iPage=13")) of the results submitted are from Ubuntu, and they all have NVIDIA and ATI cards.

So next time you want to argue, do your research first!

[quote=Aubergines] *edit: besides this is going a hell of a lot off topic from nuclearpidgeon's orignal post :razz:*[/quote]
True dat.

*edit: RE your comment about [Opensuse]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=distribution&sReturnToTitle=View%20Distributions&sTitle=View+Distributions&iItemsPerPage=25&iPage=9&sOrderBy=name&bAscending=true&iItemsPerPage=25&iPage=8") and [Debian]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=distribution&sReturnToTitle=View%20Distributions&sTitle=View+Distributions&iItemsPerPage=25&iPage=5&sOrderBy=name&bAscending=true&iItemsPerPage=25&iPage=2")...*

---

### Post by nuclearpidgeon on 2009-04-13
Hmm. just ran the install again and it failed once again. However, I noted that it failed whilst configuring the hardware. I've attached a backup of the entire /var/log directory if you need any log files - I was going to also upload the syslog, but it was too big to upload separately so you'll have to go through the zip file.

Out of interest, here's the dump from the /var/log/installer/debug file:

[quote=/var/log/installer/debug]Ubiquity 1.11.20
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:192: PangoWarning: error opening config file '/root/.pangorc': Permission denied

  self.glade = gtk.glade.XML('%s/ubiquity.glade' % GLADEDIR)
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:107: GtkWarning: gtk_scrolled_window_add(): cannot add non scrollable widget use gtk_scrolled_window_add_with_viewport() instead
  gladexml = gtk.glade.XML(gladefile, name)
Ubiquity 1.11.20
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:192: PangoWarning: error opening config file '/root/.pangorc': Permission denied

  self.glade = gtk.glade.XML('%s/ubiquity.glade' % GLADEDIR)
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:107: GtkWarning: gtk_scrolled_window_add(): cannot add non scrollable widget use gtk_scrolled_window_add_with_viewport() instead
  gladexml = gtk.glade.XML(gladefile, name)
partition: ('1', '32256-214745610239', '214745577984', 'primary', 'ntfs', '/dev/sda1', '')
partition: ('5', '214745642496-248559736319', '33814093824', 'logical', 'ext4', '/dev/sda5', '')
partition: ('6', '248559768576-250056737279', '1496968704', 'logical', 'linux-swap', '/dev/sda6', '')
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:2554: GtkWarning: gtk_cell_layout_set_attributes: assertion `GTK_IS_CELL_RENDERER (cell)' failed
  self.grub_device_entry.set_text_column(0)
ubiquity: Fatal IO error 104 (Connection reset by peer) on X server :0.0.[/quote]
it shows the crashing of X, but I can't seem to understand why...

---

### Post by nuclearpidgeon on 2009-04-19
I've downloaded the Release Candidate and installed again and encountered no issues whatsoever.

I reckon there was a problem with the display driver and the installer, but whatever it was is gone now

Thanks for your help anyway!

---


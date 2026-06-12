---
title: "Ubuntu 10.10, one step forward; one step back"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by george3095 on 2010-11-23
I would like the people who worked preparing 10.10 to know that I really appreciate their efforts. I am a user; meaning I don't write code, but I know when something's wrong. Here're a few observations that I send because I hope they will be taken constructively:

1. Even though I checked to make updates along with the installation, they didn't happen until after the first reboot.
2. My optical mouse's pointer is off the vertical mark by about a quarter inch above where it should be. I don't have a clue how to fix this.
3. Shortly after installing 10.04, I was advised that a 3rd party driver was available for my computer. It hasn't happened yet with 10.10 and I'm unsure which of the available drivers is the correct one for my video card.
4. My window is larger than the monitor's screen size and I don't know how to fix it. This was possible to fix with, gosh, one of the 9.something-or-other Ubuntus when I first explored an OS other than MS Windows.

My sense is that, when Ubuntu should be getting more and more polished, refined, easier and easier to install with every succeeding release, what seems to be happening is not that. I apologize if I ruffled anyone's feathers.

---

### Post by davidmohammed on 2010-11-23
remember 10.10 is not a LTS release - so it is more "cutting edge" - but still more rough around the edges than the 10.04 release.

Developers rarely read forums - so for any issues and suggestions suggest, create a launchpad account and file a bug report.

---

### Post by tommcd on 2010-11-23
> **george3095 said:**
> 
1. Even though I checked to make updates along with the installation, they didn't happen until after the first reboot.
Your internet access may not have been enabled during the install.
> **george3095 said:**
> 
3. Shortly after installing 10.04, I was advised that a 3rd party driver was available for my computer. It hasn't happened yet with 10.10 and I'm unsure which of the available drivers is the correct one for my video card.
If you could tell us what video card you have, perhaps we could provide instruction on how to install the driver. If you keep the video card you are using a secret, how do you expect anyone to help with this?
> **george3095 said:**
> 
4. My window is larger than the monitor's screen size and I don't know how to fix it.
What is the native resolution for your monitor? And what resolution is Ubuntu currently giving you?
If installing the proper video card driver does not fix this, you may be able to fix this with **xrandr**:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
Or you may be able to fix it by setting the proper Horizontal Sync and Vertical Refresh in your xorg.conf file.

---

### Post by george3095 on 2010-11-24
TOMMCD, thanks for your comments. About my Internet access being or not being enabled during the installation of 10.10: I can't say either way. It seems logical to me that if the option was offered to download updates along with the installation, why should one not expect that enabling Internet access early on was provided?

As for the video system (yes, it is old), it is an Nvidia GeForce4 MX Integrated GPU. BTW, I just downloaded the Linux driver for my GeForce4 from Nvidia. It has a .RUN extension, so now I've got to learn how to make it work. But, I'll wait until you have a chance to respond before I blow something up.

And, as for the video size, for mysterious reasons, the window now fits the screen, just as the mouse pointer now points exactly where it should (but, all this happened with the second installation, which, by the way, is still running and I'm stumbling upon tweaks here and there).

The native resolution is of my monitor is 1024 x 768, but I get that from the monitor manual. I think that until I get the correct driver installed, I won't be able to see what resolution is being displayed.

---

### Post by tommcd on 2010-11-24
> **george3095 said:**
> 
As for the video system (yes, it is old), it is an Nvidia GeForce4 MX Integrated GPU. BTW, I just downloaded the Linux driver for my GeForce4 from Nvidia. It has a .RUN extension, so now I've got to learn how to make it work. But, I'll wait until you have a chance to respond before I blow something up.

Your video card uses the nvidia-96 driver. According to the Ubuntu 10.10 release notes, the nvidia 173 and 96 drivers were not compatible with the Xorg 1.9 that shipped with Ubuntu 10.10:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)
This issue was fixed with the 173 driver that is available in the Ubuntu repos. I do not know if the 96 driver in the Ubuntu repos has fixed this issue or not.
The current nvidia 96.43.19 from nvidia.com says that it fixed the incompatibility with Xorg 1.9. The 96 driver in the Ubuntu repos is 96.43.18 though:
[http://packages.ubuntu.com/maverick/nvidia-96](http://packages.ubuntu.com/maverick/nvidia-96)
When you go to: system > administration > additional drivers, does it offer to install the nvidia driver from the Ubuntu repos. If so, is it the 96 driver?
I think your best bet may be to try the driver from nvidia.com. See this from Ubuntu-Geek [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)
As far as I know, if you want to install the nvidia driver from nvidia.com, you still need to install the *linux-headers* for your kernel and the *build-essential* packages as it says here:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) 
Your other option would be to stick with the nouveau driver that is the default with Ubuntu. The open source nouveau driver should work ok with your older nvidia card.
I hope all of this has not confused you too much.

---

### Post by george3095 on 2010-11-25
TOMMCD,

QUOTE: Your video card uses the nvidia-96 driver.

I installed the 96 driver and found it was "activated but not in use." Things went downhill after that. I'll bypass all the steps I took to where I am.

After a reboot, the computer opened in Terminal and that's where it is at the moment. I've fallen and I can't get up. From the Ubuntu forum, I came across "sudo apt-get install ubuntu-desktop" and learned I had the latest. Then I tried "sudo apt-get ubuntu-desktop" and got nothing. I've been here before. It was just my inability to get out of Terminal that made me re-install 10.10 the second time. Looks like a third re-install is in my future. Since I know nothing much about navigating Terminal, I'm at full stop.

Quote: When you go to: system > administration > additional drivers, does it offer to install the nvidia driver from the Ubuntu repos.

No. Unless I first install 96, nothing shows up. After 96, going to an Nvidia set up utility tells me what to do but the commands are for Terminal. There, I know nothing.

If I can stumble on getting out of terminal and into the GUI, then I may not need to re-install.

QUOTE: I hope all of this has not confused you too much.

Nope. It's just that I never learned operating from the Command line (Terminal to you), so I'm sort of wandering.

Thanks for all your help. It's the collaborative effort of the community that has made Linux so popular.

---

### Post by tommcd on 2010-11-26
> **george3095 said:**
> 
I installed the 96 driver and found it was "activated but not in use." Things went downhill after that. I'll bypass all the steps I took to where I am.
After a reboot, the computer opened in Terminal and that's where it is at the moment. 

I was afraid this would happen due to the incompatibility with Xorg 1.9 and nvidia-96.
How did you install the nvidia 96 driver? Did you install the driver from nvidia.com? Or did you install the driver from the Ubuntu repos?
In either case, check your xorg.conf file. You can open it in the terminal using the *less* command:
```
less /etc/X11/xorg.conf
```
Then scroll through the file with the arrow keys. Check the **Section "Device"** section and be sure the driver is listed as "nvidia". You can quit out of *less* by hitting the "q" key.
 If the driver is not listed as "nvidia", you can change it using the *nano* text editor:
```
sudo nano /etc/X11/xorg.conf
```
Then when you are done editing hit Ctrl + X, then Y to save the file in *nano*. If you mess up the editing and want to quit without saving, hit N instead of Y. 
Also, if you installed the driver from nvidia.com, did you blacklist all the stuff in */etc/modprobe.d/blacklist.conf* that is says to blacklist in the tutorial I linked to:
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)
If you installed the driver from the Ubuntu repo, just remove it:
```
sudo apt-get remove --purge nvidia-*
```
You can also easily remove the driver from nvidia.com if you want:
```
sudo sh NVIDIA-XXX --uninstall
```
 Where XXX is the driver number that you installed.
So write back with which driver you installed (nvidia.com or Ubuntu repos) and we can go from there.

---


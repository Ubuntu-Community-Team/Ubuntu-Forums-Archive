---
title: "Installed Ubuntu 7.10 on Virtual PC 2007 &amp; Mouse works"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Othelo on 2007-10-24
First of all, this is not my work. I found this article earlier today and decided to try it out myself. I'm new to the whole Ubuntu scene and I followed the instructions with the screen-shots he included (use the link below to get the whole idea) and I was able to install it on my AMD Athlon 1 GHz with 1GB of RAM. I know it's an old pc, but the point is, I got it to install and my mouse actually works.

The one thing that I did find that wasn't included with his article is that, once it's installed, the vpc won't connect to the LAN. Here's the way to resolve that issue in case it's hasn't been discussed:

System - Preference - Network Proxy - Advanced Configuration tab:
Remove the following:
localhost
127.0.0.0/8
*.local

Here's the link to the article because I need/want to give credit where credit is due:
[http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/]("http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/")

Installing Ubuntu 7.10 Under Virtual PC 2007
October 18th, 2007 — arcanecode 
Ubuntu version 7.10 was just released. In keeping up with tradition I’d like to describe step by step instructions on how to install and get it running under Virtual PC 2007.

Before I begin though, I’d like to give a word of thanks to all the folks who have commented on my previous postings. It was their findings and efforts that helped to create this work, I owe them a big thanks.

OK, first thing you need is to download the Desktop install ISO from the Ubuntu site ([http://www.ubuntu.com](http://www.ubuntu.com)). You can skip right to the download mirrors page at [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) if you want to save a few mouse clicks.

Once you get it downloaded fire up Virtual PC, and create a new machine. If you are not familiar with VPC, see my step by step instructions for creating a machine at [http://arcanecode.wordpress.com/2006/09/20/virtual-pc-step-by-step/](http://arcanecode.wordpress.com/2006/09/20/virtual-pc-step-by-step/) Make sure to pick “other” as the OS type. I used 512 meg of ram because my system has 2 gig, but if you have less you can get away with 256 meg of ram for the Ubuntu Virtual machine.

Fire up your new virtual machine, and use the option in the CD menu to “Capture ISO image”. Point the image at the desktop iso you just downloaded.When it starts, immediately press the down arrow, so that “Start Ubuntu in Safe Graphics Mode” is highlighted.

When 7.04 was released, the new kernel had issues with the mouse emulated by Virtual PC. To be blunt, the mouse just didn’t work. However, several work arounds were found. The easiest was brought to my attention via comments on the blog, the i8042.noloop option. That’s what we’ll implement, so we can use the mouse during the “live mode”.

Hit the F6 key, for Options. When the line appears, at the very end type in a space (if there’s not one after the two dashes) then i8042.noloop . Your screen should look something like this:



Press Enter to start the launch process. Be patient, it takes quite a while. Once it’s finally up though, you’ll see this screen:



Double click on the Install icon to begin the install.

On the first screen, below, you are welcomed and asked about a language. Pick your language and hit Forward.



Now pick your time zone, since I’m in the Central zone I picked Chicago as a city in my time zone and clicked Forward.



No it asks about keyboard layout, pick your keyboard if yours isn’t US English, then press Forward.



Ubuntu will crank and grind for a minute, then you’ll see this dialog asking about your disks. Just take the defaults and click Forward.



Time for a little personal info, give your name, a login id, enter the password you want to use, and what you want to name the “computer”. When done click Forward.



OK, you’re almost ready to start the install process. Look this over, if everything looks good just press the Install button and we’re off to the races.



Did I say races? Well, turtle race might be more like it, the install runs pretty slow, so get some coffee, or maybe a second bowl of ice cream if you’re doing a late night install.



I did encounter one error during the install. You may see this as well, but you can go back later and correct this through the normal updates process.



Now Ubuntu will finish, and ask if we want to reboot. Tell it no, then reboot by shutting down by pressing the red shut down icon in the very upper right of the Ubuntu window.

OK, you’ll have to be very quick with this next step. Remember the mouse issue? We’ll still need to fix it. First, boot the new machine, after clicking on CD and releasing the ISO if it’s still held. Now when you see the words “Grub loader” hit the Escape key. If you were fast enough, you’ll see this screen.



With the line you see selected, press the “e” to edit the line. Now a new screen will appear.



Move the highlight down one to the Kernal line, and press “e” to edit that line. When the new screen appears, you’ll need to add two dashes, then the i8042.noloop command. Your screen should look like this:



Press Enter, then when you are returned to the screen with “kernel…” on it, make sure the kernel line is still highlighted and press b to boot.

Once booted, login using your user id and password. When Unbuntu is up, it’s time to fix the mouse issue once and for all. Click on Applications, Accessories, Terminal. When the terminal window appears, type in:

sudo gedit /boot/grub/menu.lst



When you press Enter you’ll be prompted for your password, enter it. An editor should appear. Scroll down to the very bottom of the text and find the line that begins with “kernel”. Add the – i8042.noloop to the end of the line, as I’ve shown below. (Note I have highlighted the line to make it easy to see, yours won’t be normally highlighted in your session.)



Save the file and exit the editor and the terminal window. When you next reboot, you should be able to just login normally, and the mouse should work.

And there you go, Ubuntu 7.10 up and running, complete with mouse, under Virtual PC 2007.

P.S. If you found this post useful, please give it a Digg so others can find the same happiness you did.

---


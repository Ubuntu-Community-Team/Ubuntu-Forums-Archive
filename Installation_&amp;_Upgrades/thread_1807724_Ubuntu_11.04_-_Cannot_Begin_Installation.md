---
title: "Ubuntu 11.04 - Cannot Begin Installation"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by Cheese Power on 2011-07-19
[COLOR="Red"]***Edit:**I have successfully installed Ubuntu 11.04 using the "nomodeset" option (Thanks goes to Quackers for pointing this out to me). I have two new questions in my next post concerning shutdown and boot selection.*[/COLOR]

Laptop: Asus G51JX-X1
Processor: Core i7-720QM
Graphics: GeForce GTS 360M
Memory: 4GB
HDD: 500GB

OS: Windows 7 Home Premium 64-bit Edition, Ubuntu 11.04 (attempting dual boot)

I've burned a boot CD. I can boot up from it which brings me to a screen like the following:

[[IMG]http://img830.imageshack.us/img830/856/ubuntufirstscreen.th.png[/IMG]](http://imageshack.us/photo/my-images/830/ubuntufirstscreen.png/)

After a few seconds the screen changes to this:

[[IMG]http://img37.imageshack.us/img37/8969/ubuntuscreen.th.jpg[/IMG]](http://imageshack.us/photo/my-images/37/ubuntuscreen.jpg/)

The five dots light up like something is in the process of being done. Then I hear a very slight pop sound in my earphones like sound was just enabled. A couple seconds later I see a screen similar to the following:

[[IMG]http://img855.imageshack.us/img855/2474/ubuntumaze.th.jpg[/IMG]](http://imageshack.us/photo/my-images/855/ubuntumaze.jpg/)

Sometimes instead of the maze-looking image, I see what looks like a my windows desktop... only if it was chopped into confetti and thrown in the air. Then take all those pieces how they land and piece them together in that fashion.

While looking around for images that I could post here to show what I saw, I found someone saying the screen in the first image allows you to see some options if you press any key. I did this and was able to select a language. Then I was taken to the options.

[[IMG]http://img807.imageshack.us/img807/2793/ubuntubootoptions.th.png[/IMG]](http://imageshack.us/photo/my-images/807/ubuntubootoptions.png/)

Afterward I tried checking the disc for defects. It said everything was good. I then tried Ubuntu without installing. I arrived at the maze screen again. The next time around I tried to install it. Again the maze screen popped up. I haven't looked to see what the F6 "Other Options" were. I decided to try asking for help first. Then while messing around on my own, I can wait for responses.

I'm not sure what to do other than mess around in the additional options. Any aid in this situation would be much appreciated.

---

### Post by Quackers on 2011-07-19
You need to use the one you have avoided so far :-)
At the above screen press F6 key and from the options that appear in the lower right of the screen choose the "nomodeset" option.

---

### Post by Cheese Power on 2011-07-19
The "nomodeset" option worked for me. What exactly did this do that allowed the installation to commence?

After the installation process, I've downloaded gparted and it looks like the drive is set up the way I wanted. First 400GB for Win7 and the last 100GB for Ubuntu.

_I've got a couple questions now. First question:_
How long is it supposed to take to restart the system from Ubuntu? Immediately after installing it wanted me to restart my machine. I proceeded to do so. I was taken to a black screen where some text said it was restarting. There were two other messages below that. Each of these three messages had an [OK] to the right of them on the screen. After a couple seconds blue text appeared telling me to remove any installation media from my disc tray, then press enter. I did this, but nothing happened. I waited about two minutes before powering down the machine.

I booted up Ubuntu again, this time from my hard drive. Everything seemed to be in place. I wanted to check to see if the windows portion was still operational, so I restarted my laptop. This time a black screen full of white text appeared. It seemed as though the text was going past the edges of the screen. Then like before, it just sat there for a period of time. After about a minute, I manually turned of the computer again.

I'll try a few more powering down options from Ubuntu, but it does seem like something is wrong. What can I do to test for possible causes?

_Second question/concern:_
Previously Windows 7 would boot up automatically. During the first splash screen when booting up, I could choose what to boot from by hitting ESC. I could then choose a drive or cd to boot from.

After installing Ubuntu, I come to a boot menu that has two boot options for Ubuntu, two memory test options, and a final option for Windows 7. If I don't select an option in a certain period of time, Ubuntu is booted by default. Is it possible to change the way I select what to boot? I'd prefer Windows automatically booting unless I press some key, allowing me to choose from a list of options (similar to the way it has been). This is just a minor convenience issue.

---

### Post by Quackers on 2011-07-19
The nomodeset option changes the parameters for the use of your graphics card.
If you needed that option to boot the live cd/usb then you will need to use that option for the first boot after installation.
The guide below explains how. You need to scroll down a little bit, to the section entitled "How to temporarily set kernel boot options on an installed OS (not wubi)"

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


When it's booted again to the desktop you should run the Additional Drivers utility and install the nvidia-current driver.

While that is downloading you can open a terminal and run ```
sudo update-grub
``` then watch the terminal screen as grub.cfg is run, where you should see the Windows Loader recognised. This should create a grub menu at startup which will give you the choice of which operating system to boot.

---


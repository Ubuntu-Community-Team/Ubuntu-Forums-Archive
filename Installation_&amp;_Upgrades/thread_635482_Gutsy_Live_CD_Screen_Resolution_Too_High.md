---
title: "Gutsy Live CD Screen Resolution Too High"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by suityou01 on 2007-12-08
I have seen this posted elsewhere. All of the suggestions do not work for me. I boot from the ubuntu live cd and select the F4 option to select a screen resolution my monitor supports (1024x768x16). Then I tell it to load the live cd and after the initial progress bar it knocks the res up to 1280x1024 which my monitor can't handle.

So the other posts suggest using the F6 option to add the words "live vga=771" to the end of the boot options string just before the two --

And that doesn't work either.

So the other suggestion was to hit F1 to get a terminal window and type the live vga string in. You don't get a terminal window you get a help menu!!
I know I am not the only one suffering this problem so there must be a suggestion that DOES work so can someone please post it?

Sorry for being cranky I'm tired and have been messing around with this all evening.

---

### Post by komputes on 2007-12-08
If the CD doesn't detect a screen resolution which is compatible with you VGA adapter or Monitor you can go into the command line interface by using combination keys. From there you can reconfigure your xserver-xorg. I would recommend you save everything before you do this because it will restart the gnome environment.

Combination Keys:
[CTRL+ALT+F1] Go To Console Mode (there are in fact 6 of there from F1 to F6)
[CTRL+ALT+F7] Go to GUI mode 

(copy/print these instructions if you don't have a second pc)

1) Press CTRL+ALT+F1 You will be prompted to authenticate yourself.

2) Once authenticated tupe the following:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

3) This will bring up a blue screen where you will be able to reconfigure the resolutions you are comfortable with. Navigate with arrows and press space to select/deselect resolutions. Tab to get you to the ok box, and press enter.

4) To restart GDM (Gnome desktop manager) type the following
```

sudo /etc/init.d/gdm stop 
```
	(stops gnome desktop manager)

```
sudo /etc/init.d/gdm start
``` 	(starts gnome desktop manager)

That should work. Of couse there is a possibility that if the live CD doesn't detect the video card driver, it will ask you to pick one from the list. This has happened to me, it showed me a list of manufacturers to pick from, sometimes it included the resolutions, other times it did not.

Hope that help you out.

[IMG]http://komputes.com/images/komputes_userbar.gif[/IMG]

---

### Post by suityou01 on 2007-12-09
A very detailed reply, thank you. Sadly I am too stupid to follow it.

Here is what happens for me.

Boot PC with Ubuntu live CD. Get initial screen with all the options on it.
Press CTRL F1. Nothing happens. Try again, nothing happens.

At what point in the proceedings should I press CTRL F1, or should I do something else?

Thanks

:(

---

### Post by jespdj on 2007-12-09
Its Ctrl + **Alt** + F1 ... F7, not Ctrl + F1 ... F7.

---

### Post by Pumalite on 2007-12-09
[http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html](http://www.linuxforums.org/forum/ubuntu-help/105368-newb-help-everything-too-big.html)

---

### Post by suityou01 on 2007-12-09
Hi thanks for your patience. I am sooooooo tired after being up all night with the little blighter (the pc not my sons).

I can confirm CTRL F1 does nothing.
I can confirm CTRL ALT F1 does nothing.

IF .... you hit enter to get it installing and THEN press CTRL ALT F1 you get a text based install screen showing you what it is loading. THEN it knocks the res up to 1280.


OMG how hard is this!

---

### Post by Pumalite on 2007-12-09
[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)
[http://ubuntuforums.org/showthread.php?t=579881](http://ubuntuforums.org/showthread.php?t=579881)
[http://ubuntuforums.org/showthread.php?t=505249](http://ubuntuforums.org/showthread.php?t=505249)
[http://ubuntuforums.org/showthread.php?t=601775](http://ubuntuforums.org/showthread.php?t=601775)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by suityou01 on 2007-12-09
I have successfully booted into the live cd in a lower res. There is more you need to know, and I got a big leg up from the previous posts but there was still a bit of trial and error that I wanted to share with the community.

Firstly boot from the live cd as normal.
When presented with the front screen listing the different install options just hit enter to install normally.
After a while (if you are having this problem) the monitor will complain of an unsupported screen resolution and go blank. It is at this point you need to press CTRL ALT F1.

Then you get a command line. To make sure press enter once.
You should be greeted with a command line like 

ubuntu@ubutnu:~$ _

Now type

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The you get a bue screen titled Configuring xserver-xorg where it will ask you to select the x server drive from the list. Currently vesa is selected but this fails to start later on so I use VGA. Once selected press enter.

Then choose your screen res from the list. I choose 1024 x 768 as this works for me, but a lower one may do if you are still having problems.

Then you are back at the command line.

I now entered the code


```
sudo /etc/init.d/gdm stop
```

You get the message
* Stopping GNOME Display Manager ...      [OK]

Now type

```
sudo /etc/init.d/gdm start
```

The first time I do this I get a fail message

* Stopping GNOME Display Manager ...      [Fail]

I try the start command again and then it works.

Then I get another blue screen with a message

"There already appers to be an X server running on display :0. Should another display number by tried? Answering now will cause GDM to attempt starting server on 0:again"

I selected YES.

Then you get dropped out to the command line again. And then the screen flickers a few times. 

Then you get a black screen with a gui box stating

"Ubuntu is running in low-graphics mode"

"Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens you have to configure the display yourself."

I click on continue and it drops me back to the command line.

Now I issue the stop and start commands again, and when given the blue screen with the warning message about display:0 I selected YES again.

It then drops me back to the command line and the screen flickers a few times. Then I get the black screen with warning dialog box again "Ubuntu is running in low-graphics mode". I click on continue.

It drops me back to a command line again. Where I wait patiently.

I issue the start command again and go through the same steps as above, and it keeps sending me back to the command line.

Eventually after 3 or 4 attempts the GNOME Desktop loads.

So that is how it is done. Good luck.:)

---

### Post by komputes on 2007-12-10
CTRL+ALT+F1...what's the technical name for that state? Terminal mode? Prompt mode?

---

### Post by komputes on 2008-01-02
In fact they are called virtual consoles. I guess they work when your resolution in X is not working. It's a good way to troubleshoot from a command line interface.

---


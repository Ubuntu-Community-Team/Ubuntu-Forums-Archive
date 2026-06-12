---
title: "hostname and root problem"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by lostinbeta on 2005-07-19
Hey,

I really hate to say this, but I'm your typical linux/ubuntu n00b.

When I installed Ubuntu I didn't set the hostname properly... and now when I log in to Ubuntu with my username I get that pop-up error that tells me my hostname is wrong or whatever and that GNOME may not perform properly.

So I choose 'log in anway' and I can't access any tools.  None of the administration tools work at all (they appear to load then disappear)... this goes for Root Terminal.

Ok, so what I can do however is start up in Ubuntus recovery mode and log-in in the command menu as root and change my hostname to localhost... that way when I log into Ubuntu I no longer get that hostname error.  When I do this and I go to the administration tools I get the password prompt (which is what is supposed to happen), but once I input my password and continue I get an error that says 'Child terminated with 1 status'.  What does this mean?  How do I correct this?

This has me aggrivated because my monitor resolution is stuck at like 640x480,  I can't connect to the internet, and my hostname in the etc/hostname file is still the wrong one (which is probably why i can't connect to the internet).  And I can't use sudo or visudo or anything with my username, and i can't use the admin tools or log in as root to modify the files to get them working correctly.

I'm kind of stuck between a rock and a hard place.  I've been rebooting and switching between my Windows Partition and my Ubuntu partition to try and fix this problem.  My Windows partition still has internet access, so I've been switching back and forth between the 2 partitions to try and fix the issue (i would search here and write stuff down and go back and try it)



[edit]
I've managed to fiddle around with it and set my default username as an admin.  This got me access into my administration tools, and I fixed my hostname issues.  I am posting this from Ubuntu so I got my internet working!  WOO HOO!

Now I gotta vix this resolution thing... ugh... 640x480 is atrocious.  I've been looking around the forum on how to do that, but i just can't seem to get mine to auto detect correctly, and the xorg.conf file seems to have my settings fine in there.

It's a Dell 17" Flat Panel LCD if that matters.
[/edit]
Do I have to reinstall Ubuntu?  I sure hope not  ](*,)

---

### Post by lostinbeta on 2005-07-20
Here is the xorg.conf information if it matters

I didn't change a thing of it, this is how it has always been

Section "Monitor"
	Identifier	"DELL E172FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL E172FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

---

### Post by ninotob on 2005-07-20
Regarding your first problem, one thing to keep around is a live-cd version of linux.  That way if something goes wrong, you can boot from the live-cd, mount your HD, and try to fix the problem from there.  Sometimes it's easier to fix things from outside the problem rather than from inside it.

But congrats on solving the riddle your own way -- half the fun of linux is solving the riddles.  ;-)

---

### Post by lostinbeta on 2005-07-20
I do have a live cd, I'm just not that smart...lol.

I still have my monitor problem, but it seems to have increased.

I've been solving my problems so far by searching the forums and piecing together tidbits I find of other peoples problems.

Well I've search about every screen resolution issue thread and i've ran dpkg-reconfigure xserver-xorg like a billion times and I finally came across someone saying something about dedicated at least like 8MB of ram to the internal video card in the BIOS... so I started and went into my BIOS and found I have nowhere to set that value in there... so I just exited my BIOS (without saving) and next thing you know when I go to log into Ubuntu I get nothing but a solid brown screen after logging in.

*sigh*  What the heck is going on?  I didn't do anything.  So needless to say I'm back on Windows.  Sheesh, if I would have known the slogan 'Linux for human beings' meant 'Linux of intelligent human beings' I wouldn't have ordered the CD.

But alas now I am determined.

So now I'm at 640x480 resolution but that doesn't matter because I get solid brown when I log in and have access to absolutely nothing (though I can use CTRL+ALT+F1 and CTRL+ALT+Backspace).

Any insight as to what I should do now?

---

### Post by mingus on 2005-07-20
This often happens when the refresh rate or color depth is too high with the resolution chosen.  The Xserver drops you down to the lower resolution to keep that display from frying.

Do $sudo dpkg-reconfigure xserver-xorg

Drop the default color depth to 16 or even 15.  At the screen resolution choose the lowest refresh rate offerred for the resolution you want, e.g., 60Hz.

---

### Post by lostinbeta on 2005-07-20
Ok, I'll give that a try, but I thought refresh rates didn't matter for LCD monitors.

Oh, and there's only one refresh rate for the resolution I want (I use 1280x1024)

---

### Post by mingus on 2005-07-20
[QUOTE=lostinbeta]Ok, I'll give that a try, but I thought refresh rates didn't matter for LCD monitors.

Oh, and there's only one refresh rate for the resolution I want (I use 1280x1024)[/QUOTE]

It is usually the color depth that is the problem.  You may be right about the refresh rate; actually I was thinking about the modeline timings.  But in terms of getting your desired resolution, there is an inter-dependency with color depth and refresh.

---

### Post by lostinbeta on 2005-07-20
I've managed to get my resolution working great using the 855resolution method mentioned in this thread...

[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

Though I had to follow the instructions in a roundabout way since I only have access to the Terminal.

I'm glad I found nano in another thread otherwise I would have no idea how to edit any config files through the terminal.

Anywho, I knocked all my problems out, except one huge one... my screen still stays solid brown when I log in!!!!

ACK!  Does anyone know why this is happening?

The 855resolution thread adds a note about X not getting displayed, but he switches to a terminal then back over to X and it works.  Well this problem existed BEFORE the 855resolution fix and switching back and forth from the terminal doesn't cure my problem.

I'm going nuts here!

---

### Post by lostinbeta on 2005-07-20
I think I'm going to repost this since it has become an entirely seperate problem from the original.

Oh, btw... this is how I fixed my original problem (in case anyone comes across this thread with the same problems).

I didn't know about nano to edit files in the terminal as root, so I'm sure you can use that to edit the hostname file.

nano /etc/hostname

What I did though, was set the permissions of the hostname file to my username (then set it back after modifying)...  You do this by being root in the terminal and using...

chown [username] /etc/hostname

..replace [username] with the username you want to provide permissions to.

Then open gedit and modify the hostname file and save.

That fixed my hostname issue... and seemed to have fixed my root issue too because I no longer had any problems after that.  So much in linux ties to your hostname...lol.

Anywho, my resolution problem as I stated was fixed with the 855resolution solution found at [http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029) .  This is the only solution I tried on this forum (after many tries found in various threads via extensive searching of this forum) that actually got my resolution to work.

On top of the 588resolution solution I also had to add my HorizSync and VertRefresh values into the Monitor section of X11/xorg.conf file.

---


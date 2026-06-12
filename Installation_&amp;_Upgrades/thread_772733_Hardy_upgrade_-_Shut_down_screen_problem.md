---
title: "Hardy upgrade - Shut down screen problem?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Popaul on 2008-04-28
Recently upgraded to Hardy. Few teething problems...
One is what happens when shutting down the PC. Under Gutsy and others, I got the Ubuntu logo and the progress bar going down, then power off.
Now I get a terminal screen showing the last logging-in words of wisdoms (finishing with Running local boot scripts (/etc/rc.local)  [OK] ), and I have to wait about 30-45 seconds then I get the following:
NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.
NetworkManager: <INFO> Caught termination signal
NetworkManager: <DEBUG> [1209404787.824467] nm_print_open_socks(): Open Sockets List:
NetworkManager: <DEBUG> [1209404787.824467] nm_print_open_socks(): Open Sockets List Done.
NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed
NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus daemon is running!

Then the PC shuts down. No big deal, but... The 2 last lines worry me. Is that important? Sign of a problem somewhere? And I would feel better if I could get my ol' shut-down Ubuntu progress bar as before.

Thank you in advance for pointing me in some sort of useful direction!

---

### Post by Popaul on 2008-04-28
Some added info...
found this thread [http://ubuntuforums.org/showthread.php?t=603054](http://ubuntuforums.org/showthread.php?t=603054)
but all suggestions in it did not work. ACPI=force in fact blocked the starting process in fact. ACPI=off did help for some other problems I got before, so I let it that way in the grub menu.
Twicking on apm did not change anything at all.
My Pc is a Compaq, dual core Intel Pentium D.
There may be also a problem with the battery (maybe linked?) as I realised that on the starting trails on the terminal screen there's a line at some point that says:
FATAL: error inserting battery (/lib/modules/2.6.24.16 generic/kernel/drivers/acpi/battery.ko): no such device

But them somewhere below there's also 
Checking battery state [OK]

Any help?

---

### Post by jery_wang2002 on 2008-04-28
I have exactly the same problem and nobody seems notice this.
It's not a big deal but it is a pain everytime I shutdown after presentation and everyone in the room looks at me for about 1 minute wondering what I was doing with my notebook.

It's not serious but it is totally annoying. the screen stuck at the text console for about 1 minute and when it resume, it shows the warning/erro messages below and soon followed with ubuntu splash with progress bar.



> **Popaul said:**
> Recently upgraded to Hardy. Few teething problems...
One is what happens when shutting down the PC. Under Gutsy and others, I got the Ubuntu logo and the progress bar going down, then power off.
Now I get a terminal screen showing the last logging-in words of wisdoms (finishing with Running local boot scripts (/etc/rc.local)  [OK] ), and I have to wait about 30-45 seconds then I get the following:
NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.
NetworkManager: <INFO> Caught termination signal
NetworkManager: <DEBUG> [1209404787.824467] nm_print_open_socks(): Open Sockets List:
NetworkManager: <DEBUG> [1209404787.824467] nm_print_open_socks(): Open Sockets List Done.
NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed
NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus daemon is running!

Then the PC shuts down. No big deal, but... The 2 last lines worry me. Is that important? Sign of a problem somewhere? And I would feel better if I could get my ol' shut-down Ubuntu progress bar as before.

Thank you in advance for pointing me in some sort of useful direction!

---

### Post by Popaul on 2008-04-29
No.... Does not work. Strange. At first it was okay, but now I have the problems back again, without changing anything. Problem is elsewhere? Anybody could provide some guidance as to where to look?



Sorted! At least on mine.
After searching on various threads and discussions on Linux sites, and zillions of shut-down, re-boot...
All is done in the grub menu (/boot/grub/menu.lst).
Start editing it by typing in a terminal:
sudo gedit /boot/grub/menu.lst

In the file, look for
## ## End Default Options ##
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c8d0d37c-d902-4a2b-a912-01df8fee6ab4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

Of course the various version numbers etc will vary with your versions.
On the "kernel" line after "ro", I have "quiet splash": this avoid to have all the command lines scrolling on the screen at start-up.
Then I added:
noapic: this is to kill a little message that appeared at start-up just before the Ubuntu progress bar, saying there was a problem with the 8254 timer being 'not connected to IO-APIC'. 
And then:
acpi=off: that is necessary with noapic. If not, the boot will stop at some point (progress bar stopped at about 1/5 from teh start).
And finally:
noapm: that stops all the garbage I got on the screen when shutting down.

Careful at the typing: only one space between each option, and no space within one option. So the end of the kernel line looks like:
...12-01df8fee6ab4(your version) ro quiet splash noapic acpi=off noapm

Of course if you have several start option in the grub menu, you should do these mods to every kernel line of each option that gives trouble.

As I understand from various threads, APIC and APM are power management tools for LAPTOPS, useless (well... I hope) for desktop. If I am right, it is a bit bad that these installed themselves automatically even on desktops without these facilities, and put a little mess everywhere. Should I understand that this is bug?

So far it seems okay, except 'perhaps' a start-up that is a bit slower than before, but that maybe me.

It's all fun!

---

### Post by Popaul on 2008-04-30
Well, while I did not get any feed-back at all on this, I spent quite many hours googling around on this. Apparently:
- this does not appear on every machine of course, so it is hardware related, but it seems apparently unique to Ubuntu (other debian distro do not have this bug);
- it cannot be fixed except by writing a patch (found one site with one, no thank you) to by-pass the nervousness of network manager;
- this did exist at the beta state of 8.04, but not fixed and the fully blown version was released, knowing full well that this bug was still there;
- while my problem is only a garbaged screen at shut-down, on some configurations it has more serious consequences. From one Linux forum:
<<After upgrading, we discovered that we couldn't connect to our corporate servers with 8.04, despite having no problems with 7.10 and previous versions...it is a showstopper>>
And the conclusion from another Linux forum:
<<...Would you want to see this on your screen? Is this how an enterprise system should be? Would you consider an operating system that has these kinds of bugs for your corporate desktops? What would the reviewers say if Microsoft released a product with this bug?
It is unbelievable that Dell would put this on their hardware. >>

I have faith. Keep using it, but yes, I will not (yet?) push Ubuntu to replace Windows for my company's system.

---

### Post by Rallg on 2008-04-30
No problem on may amd64 terminal upgrade (from beta version), but I do see some shutdown garbage on the i386 version (installed from CD). I didn't see it before when beta-testing i386. Although I don't have the same messages as you do, nevertheless there is no difficulty other than annoying messages at shutdown (to my knowledge).

I am wondering if those messages are always there, but normally we don't see them due to screen erasure, now disabled? Just a guess. If you've ever tried a Linux version that doesn't use a boot sceen, then you've seen plenty of cryptic messages, some of which sound bad but really don't matter.

---

### Post by ibanez on 2008-04-30
I've had this on three machines since I believe Alpha 5, one is a P4 , the other two are 64bit , one intel one AMD. The machine I'm on now had it whilst on the dev releases ,since then I've fresh installed using the current ISO, Still the same problem .

What with the screw ups with detecting my Envy based soundcard , ( stuck on onboard sound for now) ( A known problem, so many with sound nightmares) & xorg taking away the ability to hand edit xorg.conf for video problems, after all the new xorg knows best!!, I'm more than a little fed up with Ubuntu ,it seems Hardy may have been rushed to release a little.

I'm trying out Arch and so far loving it, it is so far for me the good experience Ubuntu used to be. 

Welcome to Winbuntu.....

---

### Post by noynac on 2008-04-30
I had the shutdown error messages in early beta, they went away about the time of the release candidate, and they are back now on a fresh install. I tried the fix suggested by Popaul, but they did not work for me. I may restore an image I made of the release-candidate install just to get rid of this problem.

---

### Post by noynac on 2008-05-01
I was able to rid my computer of the error messages on reboot/shutdown and thought I would explain what I did. I made two changes and don't know which was the fix (if either), so I'll mention both.

My computer has two ethernet ports--one is built into the motherboard and the other is on a card. The first is attached to the internet (Roadrunner); the other is unused. I went to the Network app and unchecked roaming for the unused port and changed the drop down list to automatic configuration.

The second change involved the Login Window tool. I clicked on the "Edit Commands" button. I then deleted the messages in quotes from the end of the halt and reboot commands. 

I've shutdown and rebooted numerous times last evening and this morning, and no error messages for now. I hope it stays that way. 

BTW, I get the impression that this problem has multiple causes, and what works for me may not work for others. Good luck everyone.

---

### Post by Popaul on 2008-05-01
I've just tried your second change. First change is not good on mine, as I have only one ethernet port, and roaming is already disabled on this one (well... it's a desktop).
So second change... it did work at the first shut down: I got the progress bar as before, and quick shut-down as it should be, as it was with Gutsy. But on the second, third... tests, it went back to garbage mode.
As you said, the fix will probably be different from one PC to the other. It should be related to hardware and/or some other software that interfere with the network manager?
There are a good deals of bug reports around this issue. And some were existing before Hardy even. But none have been fixed so far, and the discussion activity on these reports is not high...

---

### Post by Popaul on 2008-05-01
noynac, you may well have hit the jack-pot. 
I played around with the Halt command and the Reboot command:
on my configuration (!... careful here)
- that I take off completely "Shut down via gdm." or not does not do anything;
- what does the trick is that I save the modification.
In a same session of Login Windows opened, I deleted the "...", save, then put it back again and save: shut-down was like in the good old days, with the normal progress bar and no garbage.
Checking with the "quiet splash" option taken off in the grub menu so that I can see what goes on, I only got "System is restarting please wait": (I was on reboot) nothing else, nothing about the network manager etc... So it does the trick... Everything shut-down nicely, at least on my machine.
The problem is that I cannot keep changing the halt and reboot command at each session. But that way be be a "tilt" for someone who knows???

---

### Post by noynac on 2008-05-01
> **Popaul said:**
> In a same session of Login Windows opened, I deleted the "...", save, then put it back again and save: shut-down was like in the good old days, with the normal progress bar and no garbage....

I didn't mention it before but I did the same thing. I don't know how that could make a difference, but I've had good shutdowns for almost a day now.

What is also a bit weird is that the same halt/reboot commmand that shuts the computer down fine in Login Window screen gives the error messages if used in a terminal window. Perhaps there's a reason for this. 

It's all pretty strange.

---

### Post by Greg T. on 2008-05-01
I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

---

### Post by dave373 on 2008-05-01
I have a problem since my Hardy upgrade causing the machine to hang when rebooting. After removing the splash option from menu.lst, I can see that all services appear to stop correctly.

The last message is "[..timestamp..]  Restarting..." And then nothing.. I have to hold the Power button until the power is cut completely.

this is the same for reboots and shutdowns..

I have tried the mentioned removal of "..." from the shutdown commmands.. no change..

Has anyone had a similar problem???

Dave

---

### Post by jery_wang2002 on 2008-05-01
And my notebook is Dell Inspiron 1520
C2D 2.5 GHz. It is mainstream Dell Notebook and definitely that hundreds of thousands are using. And maybe 99.99 % is on Vista/XP.

> **Popaul said:**
> It is unbelievable that Dell would put this on their hardware. >>

I have faith. Keep using it, but yes, I will not (yet?) push Ubuntu to replace Windows for my company's system.

---

### Post by jery_wang2002 on 2008-05-02
Yes, this is the fix to -slow shutdown, throwing error text- 
I can confirm that this fixes the bug.

> **Greg T. said:**
> I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

---

### Post by 1mikelli1 on 2008-05-02
i did the edit commands in login and network off roaming this solved the problem

---

### Post by agaudio on 2008-05-02
I tried the changes to roaming and to the login window, and it worked the first time I shut down. Just as popaul says, you have to make the change to the login window each session in order to keep the problem from coming back. How odd is that? Anyone have any thoughts on a more permanent solution?

---

### Post by agaudio on 2008-05-02
The plot thickens.... I think I have found at least one permanent solution.

In the Login Window dialog, under the Local tab, I changed Style from "Themed with browser" to "Plain with browser". Left everything else the same. Since then, I have done 4 restarts and one full shutdown and the problem has not come back.

I am starting to wonder if this problem is not related to another problem I was working on yesterday. I had noticed that in Hardy, the login screen had a resolution of 1600 X 1200 whereas all the user accounts on the system had 1280 X 1024. This resulted in much of the login screen not being visible. I had seen a tip somewhere that you could use "Plain with browser" to solve this problem. But then today I discovered I could change the screen settings for the Virtual mode in /etc/X11/xorg.conf to 1280 X 1024 and everything was fine, so I changed back to "Themed with browser" and selected the Human themed browser. It feels like somehow this should all be related....

---

### Post by Popaul on 2008-05-02
agaudio, I have also this problem of the login screen being too big for ... the screen. But I cannot find anything about virtual mode in the xorg.conf file. Could you give some details please?

---

### Post by agaudio on 2008-05-02
Sorry. Of course. What I ultimately ended up doing to solve the problem with my login screen being too large was to open the xorg conf file:

sudo gedit /etc/X11/xorg.conf

Then, there should be a section in the file that more or less looks like this:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@60"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

```

Previously, next to the Virtual setting, I had 1600 1280. This is what made the login screen have too high a resolution. I just changed to 1280 1024 and the problem was solved.

Hope that helps. Did you try changing the style in the login window to see if that provides a more permanent solution to the messy shutdowns?

---

### Post by Popaul on 2008-05-02
Thank you! I did not have any "Virtual" line in my xorg file. So I added it as you described and now it's okay, the login screen fits. 
Regarding the shut-down problem... actually, now it is okay. Yesterday I did quite a few start/shut cycles, always the same (deleting and re-writing the text in "..." in the same "Login Windows" dialog session, and at one point it stuck: without touching the dialog anymore, I was able to get the proper shut-down screen.
Now I did the modif you described, switching the "local" style to "plain" and I got the garbaged shut-down. So switched back to "themed" style, and got back the normal and smooth shut-down. And now it seems to be okay again. As you say, this shut-down problem seems very much related to the login set-up files...
Again, as I am using a desktop, all this verbage about Network Manager should not come up anyway as it is related only to laptop. I got also a little error previously about the "battery" (FATAL:error inserting the battery...) and of course there's no battery. I got rid of that by adding "ACPI=force" in the kernel line of the grub menu. All this seems related, as the type of PC may be detected during login I suppose.

---

### Post by Nythain on 2008-05-03
ok, now lets see if anyone can come up with how to fix this problem with kdm/kde since im having the same problems as you all, but dont have the same options :(

im sure i have the equivalent buried somewhere in kcontrol, anyone have any clues???

---

### Post by neutrino82 on 2008-05-04
Hi. I installed Hardy today on my Dell 640m and seems I have the same shutdown problem. After pressing shutdown or reboot desktop icons and bars disappear but system hangs showing the wallpaper picture and I have to press shutdown button or Crl-Alt-Backspace to complete  the shutdown process. 
Typing "sudo halt" in the terminal works and no system hang is observed.

---

### Post by neutrino82 on 2008-05-04
I found that the cause of my problem was a little program I installed "keytouch" that for some reason prevented gnome session to end. Uninstalling it made shutdown work in my case. Hope this can help even if maybe this is not related with the problem encountered by other people in this thread.

---

### Post by Tom--d on 2008-05-04
> **Greg T. said:**
> I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.



YAY :D
That did it!
My shutdowns and reboots are a matter of seconds, not minutes. 

I recommend this :)

---

### Post by laffinet on 2008-05-05
> **Greg T. said:**
> Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

Fantastic. Worked like a charm for me (lenovo R61i laptop with 8.04 on it). Finally I got rid of the annoying wait on shut down and reboot. Thanks a lot !

---

### Post by pistos on 2008-05-06
Worked for me too. Thank you!

---

### Post by darkshado on 2008-05-06
Yeah, but when you do a "ctrl+alt+backspace", the problem comes back! :(

---

### Post by pistos on 2008-05-06
> **darkshado said:**
> Yeah, but when you do a "ctrl+alt+backspace", the problem comes back! :(

I have not noticed that behavior on my machine as yet. :confused:

---

### Post by Xiong Chiamiov on 2008-05-10
> **Nythain said:**
> ok, now lets see if anyone can come up with how to fix this problem with kdm/kde since im having the same problems as you all, but dont have the same options :(

im sure i have the equivalent buried somewhere in kcontrol, anyone have any clues???
I'm waiting too :(.

---

### Post by k1ngb0b0 on 2008-05-10
> **Greg T. said:**
> I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

Thanks a lot for this.  I was wondering how to fix the problem and thankfully I ended up here.

A couple of questions though...

What would make you think to do this?  and how long will this fix....Stay fixed?  Will I keep having to do this every startup?



Thanks again :)

---

### Post by Partyboi2 on 2008-05-10
I had this same problem but all I needed to do was remove "Shut Down via gdm."  from the halt option. Since doing this ubuntu shuts down or reboots without any problems and seems to be a permanent fix to my problem.  I have tried re adding "Shut Down via gdm." to the halt option to see what happens and the system shutsdown as its meant to. So what does "Shut Down via gdm." do?

---

### Post by Bill_MI on 2008-05-10
I can add to this bunch.  Hardy shutdown gets fixed if I set a static IP for the box, which I always do (eventually).

When first installed, I set a static IP like I always do and never had a shutdown problem (I had a static IP).  I reinstalled Hardy for another reason AND HAD THE SHUTDOWN PROBLEM.  Eventually I set a static IP and viola!... the shutdown problem is history.

Obviously, all these bandaids have a root cause.  This is just MY bandaid. :)

---

### Post by girishsasikumar on 2008-05-11
I too had this shut down problem on my Acer 4152 Laptop....
post #13 solved my problem.....
Thanxxxxx

---

### Post by girishsasikumar on 2008-05-11
Well the solution stated in Post #13 does work, but the problem as others have pointed out is that it needs to be done everytime u restart or halt the system, and thatz buggy. I felt that there must be some problem with the reboot and shutdown scripts and did play around with them a bit and it soved the problem. But I am not a linux expert so cant tell why it works. Any this is what I did.

In */etc/init.d* there is a file by the name *reboot* which is the script for rebooting the system..........well thatz what I feel......if itz wrong plz do correct me.........There is a line of code in it
*reboot -d -f -i* which seems to be the problem maker..........
for those of you who have the problem with the network not stopping correctly due to which the system does not reboot or halt I suggest remove the last part of the line * -i* which tries to iteratively stop the network devices. That should solve most of the problem.

Another solution that works on system is to change that line of code with
*/sbin/shutdown -r now*

well and a funny thing about the reboot command is that in its man page there is no description about the command modifier *-d* which points to something buggy in its coding ?????

---

### Post by Xiong Chiamiov on 2008-05-11
Thank you very much.  I haven't had problems with rebooting, only shutting down (no idea why), so in the file /etc/init.d/halt I changed the line
```

halt -d -f -i $poweroff $hddown

```
to
```

halt -d -f $poweroff $hddown

```
and my computer shut down for the first time in a week (or two, or whatever).  It's rather amazing, and it's *buntu generic.

---

### Post by Xiong Chiamiov on 2008-05-11
> **girishsasikumar said:**
> 
well and a funny thing about the reboot command is that in its man page there is no description about the command modifier *-d* which points to something buggy in its coding ?????

```

man reboot
...
       /sbin/reboot [-n] [-w] [-d] [-f] [-i]
...
-d     Don’t write the wtmp record. The -n flag implies -d.

```

Not that I know what that means, but the -d flag *is* for real.

---

### Post by Nythain on 2008-05-11
cant wait to give it a try, thanks for the infos and heads up

---

### Post by Bill_MI on 2008-05-11
Fascinating.  I suspect reboot option "-i" in the scripts is on top of what I'm seeing, too.

I first discover if I have a mounted windows share I get the slow shutdown.  This is a share in /mnt, cifs via a mount command (not the Nautilus stuff).  Just a umount prevents the slow shutdown.

Next, I discover as long as NetManager is not set to this "Roaming Mode" (whatever the heck that is) then all is well again, too.  Even set straight DHCP or STATIC IP is ok - only "Roaming" gets the slow shutdown.

The terminal message during slow shutdown:
[ ***.****] CIFS VFS: server not responding
[ ***.****] CIFS VFS: No response for cmd 50 mid 11 (or 9)

More things I see:

I'd like to understand more before hacking at /etc/init.d scripts.  BUT...

Man page says on the reboot -i option: "On Linux, this is unnecessary as the kernel will do this anyway."  Hmmm...

And YES... why doesn't the packaged man page for reboot NOT cover -d?  Is this just some sloppy packaging?

---

### Post by Boktai1000 on 2008-05-11
> **Greg T. said:**
> I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

I'm currently experiencing the shutdown/reboot problem on Ubuntu 8.04... but I'm not really able to understanding what your trying to say here... if someone could just copy and paste what the command should say instead of saying what needs to be changed, or post a picture showing the entire command for shutdown and reboot I would be very grateful :) thanks.

---

### Post by Xiong Chiamiov on 2008-05-11
> **Boktai1000 said:**
> I'm currently experiencing the shutdown/reboot problem on Ubuntu 8.04... but I'm not really able to understanding what your trying to say here... if someone could just copy and paste what the command should say instead of saying what needs to be changed, or post a picture showing the entire command for shutdown and reboot I would be very grateful :) thanks.
I'm can't help you with that one, since I don't use GNOME, but I know that [this]("http://ubuntuforums.org/showthread.php?t=772733&page=4#36") fix worked for me.

---

### Post by Drakkor on 2008-05-13
> **Greg T. said:**
> I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

Thanks,Greg it finally works !

---

### Post by Xiong Chiamiov on 2008-05-13
Someone just posted another solution on the launchpad entry, which involves not using Network Manager at all.  See it [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691/comments/48").

---

### Post by ~Nightingale~ on 2008-05-15
> **Greg T. said:**
> I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU 
Note: those where all typed by hand to show my gratitude, as this problem has been plaguing me for ages

---

### Post by ~Nightingale~ on 2008-05-15
DAMN, IT ISN'T WORKING!!!!!!!!!!!!!!! WHY?!?!?!?!?!?!?!?!?:mad::mad::mad::mad::mad::mad:

---

### Post by anuban on 2008-05-16
> **Greg T. said:**
> I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

First of all thanks a lot for this explanation which solved the nuissance I was facing for so many days.
Now as I did the changes I realized that there was something to add to it...It just doesn't work as it is (at least for me)

[LIST]
[*]If you are not using Compiz advanced settings or if you have 'None' selected in Appearance>Visual Effects, then this solution works as it is.  No change.
[*]If you are using Compiz advanced setting or if you have enabled different window manager then this solution won't solve your problem just like that.  You have to do the following to make it work for you:
[LIST]
[*]Select 'None' in System > Preferences > Appearance > Visual Effects.
[*]Restart your computer.
[*]Now apply the solution.  Hopefully it will work as it is and you will no longer see that error while logout and logout time will reduce drastically.
[*]Now you can change the appearance once again if you like and use advance CCSM or whatever.
[*]I will suggest doing several restarts to see if the solution works for you before enabling advance Compiz settings.
[/LIST]
[/LIST]
Hope that helps who are still facing this Network Manager error issue while logout.:)

Thanks

---

### Post by dale_nx26 on 2008-05-17
YAY! The login solution works for me. Note: Compiz was off for me but i can't confirm its effect on this solution

---

### Post by Tom--d on 2008-05-20
As I connect to the interent by a small script running at start up, I uninstalled gnome-network-manager and network-manager.

ALL errors have now gone!
I have not had them for many weeks now :D

When I shutdown.. it just goes straight to the usplash :D

---

### Post by nimes on 2008-05-22
> **Xiong Chiamiov said:**
> Thank you very much.  I haven't had problems with rebooting, only shutting down (no idea why), so in the file /etc/init.d/halt I changed the line
```

halt -d -f -i $poweroff $hddown

```
to
```

halt -d -f $poweroff $hddown

```
and my computer shut down for the first time in a week (or two, or whatever).  It's rather amazing, and it's *buntu generic.


it's work !!!

thank you, thank you...

---

### Post by SneakyWho_am_i on 2008-05-25
Oh goodness gracious me!!

Screen (and key lock indicators) jam up on reboot/logout/etc?
Check.

Login screen at a resolution my display can't render?
Check.

This thread is solid gold!! I thought I was the only one!
Thanks, everyone!

---

### Post by alexgieg on 2008-05-25
Following the instruction in this thread, including disabling Network Manager, didn't solve the halt at shutdown/reboot for me. But I've found something that might be a piece of the puzzle as yesterday, for the first time since installing Hardy, my computer managed to shutdown properly, what I hope will happen more from now on.

The symptoms before disabling Network Manager were seeing the same dbus/libhal message others mentioned, but on a separate terminal (tty8, I think), the one I think X usually runs in, with the standard shutdown text (those lines followed by "[OK]") appearing on tty7. Afterwards, no text on 8, the shutdown one on 7, but no actual shutting down. In any case, the keyboard was mad: I could Alt-Fn to look at other screens, but not type on them, only on tty7, where it was roughly useless as there was no login prompt there to take advantage of. The good thing is that typing Ctrl-Alt-Del while there managed to restart the shutdown process and, after some more text, actually shutdown the computer.

What I did yesterday, though, was to remove the old universe "esound" package, and have the full fledged Pulse Audio system (which runs entirely in user space, not as a system daemon, what might have been the key for this) installed and working by following all the instructions from [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739).

It worked well, and as a *possible* bonus, as I said, my computer managed to shutdown properly. So, this is something you might be interested in trying yourself.

I'll keep "shutdowning" for a few more days, then re-enabling Network Manager and try a few more times, and will report back with the results and anything else I find.

---

### Post by hotweiss on 2008-05-31
> **Greg T. said:**
> I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

Hmmm, how do I do this in Kubuntu?

---

### Post by run1206 on 2008-06-05
i have tried all above situations (cutting and pasting the "shutdown via gdm" message, removing the old kernals [but kept 17 just in case], editing the shutdown and restart scripts, and did plain login instead of themed browser) and STILL my computer hangs at shutdown :cry:
(i'm on a toshiba satellite A55 btw...)

any other suggestions on what might be the culprit to the shutdown not completing? :?

thanks in advance..

---

### Post by Jack Crossen on 2008-06-06
I reinstalled "usplash" and "usplash-theme-ubuntu" using the synaptic package manager and that appears to have fixed the "scrolling text during shut down" issue on a Dell Inspiron E1405 laptop.

---

### Post by Drakkor on 2008-06-06
Hey, jack,that worked for me too, but I had it fixed before,and I guess with new kernel image updates,it goes back to the same old,lol :)

---

### Post by Dr.Ninethousand on 2008-06-10
killing networkmanager worked for me too, as far as getting rid of those error messages..  can't tell that it made anything faster though..  and I have no exit splash screen..

---

### Post by HStoic on 2008-06-15
> **Bill_MI said:**
> Fascinating.  I suspect reboot option "-i" in the scripts is on top of what I'm seeing, too.

I first discover if I have a mounted windows share I get the slow shutdown.  This is a share in /mnt, cifs via a mount command (not the Nautilus stuff).  Just a umount prevents the slow shutdown.

Next, I discover as long as NetManager is not set to this "Roaming Mode" (whatever the heck that is) then all is well again, too.  Even set straight DHCP or STATIC IP is ok - only "Roaming" gets the slow shutdown.

The terminal message during slow shutdown:
[ ***.****] CIFS VFS: server not responding
[ ***.****] CIFS VFS: No response for cmd 50 mid 11 (or 9)

More things I see:

I'd like to understand more before hacking at /etc/init.d scripts.  BUT...

Man page says on the reboot -i option: "On Linux, this is unnecessary as the kernel will do this anyway."  Hmmm...

And YES... why doesn't the packaged man page for reboot NOT cover -d?  Is this just some sloppy packaging?
My experience was similar, perhaps identical to Bill_MI's. I got slow, error-filled shutdowns whenever I had mounted a Samba share at /mnt/remoteShareName. But the shutdown proceeded cleanly if I first unmounted by "sudo umount /mnt/remoteShareName". But since I didn't want to bother issuing the umount command before every shutdown I instead tried disabling "Roaming Mode" (and selecting DHCP configuration) in System>Administration>Network and that appears to work. IOW, I now get clean shutdowns automatically, every time. (So far)

---

### Post by rjmdomingo2003 on 2008-06-22
> **Xiong Chiamiov said:**
> Thank you very much.  I haven't had problems with rebooting, only shutting down (no idea why), so in the file /etc/init.d/halt I changed the line
```

halt -d -f -i $poweroff $hddown

```
to
```

halt -d -f $poweroff $hddown

```
and my computer shut down for the first time in a week (or two, or whatever).  It's rather amazing, and it's *buntu generic.
This worked for me! Thanks a lot!

---

### Post by alexgieg on 2008-06-22
> **alexgieg said:**
> Following the instruction in this thread, including disabling Network Manager, didn't solve the halt at shutdown/reboot for me. . .

The above attempt by me didn't work. After one day, my computer stopped shutting down properly. But I didn't manage to make further tests afterwards, as I didn't have time. Furthermore, this week my hard disk crashed, so any test I might yet want to do is now impossible.

In any case, what I can report is that in my new hard disk a fresh, clean install of Ubuntu 8.04 I've been using since a few days doesn't show the halting problem at all. Thus, if you're still having problems, this Microsoft'ish route is one you might want trying:

Backup **only** your data, e-mails etc., **not** your settings, be them system setting or even /home user settings, so that every small bit of configuration is left to the newest Ubuntu installers. Erase your hard disk or, if you're lucky enough to have set separate data partitions, your system partitions. Reinstall from scratch. Create new users for a new usage. Recover your data to your new users' folders. Enjoy.

Your mileage may vary, but for me this worked, even if I didn't do it willingly. :)

---

### Post by windtracekimo on 2008-06-28
Hi, dear all:
  I have suffered from this problem for a long time.
But I found out another reason for this problem: some system service entries in /etc/rcx.d/ are not automatically cleaned when you uninstall the software.
For example, I uninstall hddtemp long long time ago, and there are still several files in /etc/rcx.d/
One solution is to use the following to remove them
```
update-rc.d -f service_name remove
```
Another way is to install sysv-rc-conf from apt-get or synaptic.
Then use it to remove those services (the previous way is more straightforward)

Hope this helps.

---

### Post by wjwh on 2008-07-03
> **Greg T. said:**
> I can confirm that this fix works for me as well. I've just tried it and had two successful reboots and two successful shutdowns in row for the first time since upgrading to Hardy. I had a bit of trouble following the shorthand references in the posts above, so I'll offer a lengthier description for those who may wish to try this.

Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

I have tried this several times but completely without success.  Clearly, this is not a universal fix for this annoying problem.  What I can't understand is why a Ubuntu version with so many bugs was ever allowed to be released!

---

### Post by run1206 on 2008-07-04
> **wjwh said:**
> I have tried this several times but completely without success.  Clearly, this is not a universal fix for this annoying problem.  What I can't understand is why a Ubuntu version with so many bugs was ever allowed to be released!

no matter what, they release a new version every 6 months.  Their are other ways to fix the similar problem, try the other solutions listed on this thread. The NetworkManager fix worked for me cuz i use "wicd" for network management.

---

### Post by Bill_MI on 2008-07-06
> **HStoic said:**
> My experience was similar, perhaps identical to Bill_MI's. I got slow, error-filled shutdowns whenever I had mounted a Samba share at /mnt/remoteShareName. But the shutdown proceeded cleanly if I first unmounted by "sudo umount /mnt/remoteShareName". But since I didn't want to bother issuing the umount command before every shutdown I instead tried disabling "Roaming Mode" (and selecting DHCP configuration) in System>Administration>Network and that appears to work. IOW, I now get clean shutdowns automatically, every time. (So far)More on this.  Just installed Hardy on my laptop and exactly as before, unmounting samba (cifs) shares that are originally mounted in fstab is my only fix.

This laptop is a wireless (b43 driver) connection and getting out of "Roaming Mode" doesn't help at all.  On the desktop it did (and still does!) but this is wired (Intel NIC)

Under no circumstances did the shutdown/reboot parameter dance show any affect.

---

### Post by wjwh on 2008-07-07
> **Bill_MI said:**
> More on this.  Just installed Hardy on my laptop and exactly as before, unmounting samba (cifs) shares that are originally mounted in fstab is my only fix.

This laptop is a wireless (b43 driver) connection and getting out of "Roaming Mode" doesn't help at all.  On the desktop it did (and still does!) but this is wired (Intel NIC)

Under no circumstances did the shutdown/reboot parameter dance show any affect.

This is another fix that has not worked for me.  I use a desktop with a wired connection and do not have "roaming mode" activated - but I still get a string of error messages on shutdown or reboot.  Surely this should be a priority fix.  As has been said before in this thread, it must be having a huge effect on Ubuntu's reputation since it is seen every time anyone gives a presentation using a Ubuntu machine!

---

### Post by jmate24 on 2008-07-09
Thanx!!!!!!!!!!:lolflag:

---

### Post by erginemr on 2008-07-10
I have also been suffering from the same shutdown screen issue, and unfortunately, none of the above proposed tricks worked for me.

However, I have stumbled upon interesting solution candidate here:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29)

>  Fix the shutdown "Network Error" display (restore shutdown splash screen)

Many Ubuntu systems have a minor bug when shutting down. Instead of displaying a splash screen indicating the progress of the shutdown process, the user is dropped out to a console screen flooded with shutdown notices (mostly network error messages). These messages are normal and expected, there is nothing to be concerned about. But it can be a bit unsightly, and it would seem that the Ubuntu team intended to have those messages hidden by the splash screen. The splash screen can be restored without much effort:

    * Go to System &#8594; Administration &#8594; Login Window, and select the Local tab
    * Select a different theme, then re-select the default theme ("Human"). This just refreshes the setting
    * Click Close, then go back to System &#8594; Administration &#8594; Login Window, and select the Local tab again
    * You'll notice that the settings are different to what you've just chosen. Restore the setting to their defaults -- Choose Selected only from the Theme drop-down box (instead of "Random from selected"), and re-select the default Ubuntu theme ("Human"). When complete, click Close. 

The setting will have saved properly this time, and the shutdown splash screen should work as intended. 

The problem is; I will be away from my home computer for some time. Those of you, who are still suffering from this bug, can you please try this as well?

---

### Post by Ozitraveller on 2008-07-12
Bingo! That worked for me. 

Thanks.

FYI: I did a fresh ubuntu alternate install last weekend using 8.04.1, so whatever is causing this problem is still there.

EDIT: Still have a slow shutdown dialog and a network-manager errors during shutdown.

---

### Post by wjwh on 2008-07-13
> **erginemr said:**
> I have also been suffering from the same shutdown screen issue, and unfortunately, none of the above proposed tricks worked for me.

However, I have stumbled upon interesting solution candidate here:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29)



The problem is; I will be away from my home computer for some time. Those of you, who are still suffering from this bug, can you please try this as well?

Unfortunately, this is yet another proposed fix which has done absolutely nothing on my machine!  It would be interesting to know if there are people for whom it has actually worked - and some details of their systems.

---

### Post by xhilyn on 2008-07-16
> **neutrino82 said:**
> I found that the cause of my problem was a little program I installed "keytouch" that for some reason prevented gnome session to end. Uninstalling it made shutdown work in my case. Hope this can help even if maybe this is not related with the problem encountered by other people in this thread.


Hi. I was having the no shut down problem which I have been trying to fix for some time as well. I had tried all the solutions but none worked for me until yours, so just wanted to say thanks as uninstalling the Keytouch prog solved my problem.

Thanks again.

xhilyn:)

---

### Post by MatthewPlanchard on 2008-07-16
> **neutrino82 said:**
> I found that the cause of my problem was a little program I installed "keytouch" that for some reason prevented gnome session to end. Uninstalling it made shutdown work in my case. Hope this can help even if maybe this is not related with the problem encountered by other people in this thread.

Thanks! That fixed it for me, too, although I'm still getting a few seconds of black screen white text before the progress bar. But the hang is no more!

---

### Post by chunder4160 on 2008-07-27
I was having the same symptoms as identified in the previous posts. I found that installing wicd and removing gnome network manager solved my problems. I now have a clean shutdown, with the splashscreen and no hangs

---

### Post by run1206 on 2008-07-27
> **chunder4160 said:**
> I was having the same symptoms as identified in the previous posts. I found that installing wicd and removing gnome network manager solved my problems. I now have a clean shutdown, with the splashscreen and no hangs

same route i took :)
good to see it works not only for me

---

### Post by wjwh on 2008-07-28
> **chunder4160 said:**
> I was having the same symptoms as identified in the previous posts. I found that installing wicd and removing gnome network manager solved my problems. I now have a clean shutdown, with the splashscreen and no hangs

This is yet another fix that has not worked for me.  True, I did not get the list of Network Manager errors any more - but I also did not get the splash screen which should be there.  I have never had this problem in any other Ubuntu distro - starting at Dapper Drake.  I am using exactly the same hardware that I was then.

---

### Post by XerXeX on 2008-07-30
I also have this annoying problem, What is "wicd" and where can I install it? Thanks!

---

### Post by whollycow on 2008-07-30
> **XerXeX said:**
> I also have this annoying problem, What is "wicd" and where can I install it? Thanks!

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

If you click on the download tab there are detailed instructions for installing in Ubuntu.  Good luck.

---

### Post by cptrsn on 2008-08-18
Experiencing the same problems as the person who started the thread. However mine seems to go a little deeper. After using Hardy for x amount of time, I can click a random botton in a terminal window, a desktop-shortcut or anything else that allows interaction after which Ubuntu will do the following:
- I get a black screen.
- Several messages about processes closing e.g. Anachronetic   
  something
- The last of these messages is the network manager.

The network manager message just hangs for god knows how long, and with ctrl+alt+backspace/delete, I get spammed with network driver not shutting down or similar. After that completes, Ubuntu switches back to show me the last bit of the unload-Ubuntu bar, before rebooting. 

This is extremely annoying as I've lost hours of work to this phenomenon. 

The reason I post this is because I didnt see anyone having the error, where it would act as described above when you click on a random icon/shortcut.

---

### Post by jajodo on 2008-09-28
> **Bill_MI said:**
> Fascinating.  I suspect reboot option "-i" in the scripts is on top of what I'm seeing, too.

I first discover if I have a mounted windows share I get the slow shutdown.  This is a share in /mnt, cifs via a mount command (not the Nautilus stuff).  Just a umount prevents the slow shutdown.

Next, I discover as long as NetManager is not set to this "Roaming Mode" (whatever the heck that is) then all is well again, too.  Even set straight DHCP or STATIC IP is ok - only "Roaming" gets the slow shutdown.

The terminal message during slow shutdown:
[ ***.****] CIFS VFS: server not responding
[ ***.****] CIFS VFS: No response for cmd 50 mid 11 (or 9)

More things I see:

I'd like to understand more before hacking at /etc/init.d scripts.  BUT...

Man page says on the reboot -i option: "On Linux, this is unnecessary as the kernel will do this anyway."  Hmmm...

And YES... why doesn't the packaged man page for reboot NOT cover -d?  Is this just some sloppy packaging?
I had the same problem as response 40 with network manager that began after editing the fstab to automount a network share.  I think network manager was floundering trying to shut down my network attached storage at reboot.

Changing the network settings of my desktop from "roaming" to "automatic" as described in other posts abbreviated but did not completely resolve the freeze up.

Then I edited the etc/init.d/reboot file as others have alluded to and this appears to have solved the problem for good.  More specifically, using sudo gedit you will see (among other things in the file)

PATH=/usr/sbin:/usr/bin:/sbin:/bin

. /lib/lsb/init-functions

do_stop () {
	# Message should end with a newline since kFreeBSD may
	# print more stuff (see #323749)
	log_action_msg "Will now restart"
	reboot -d -f -i

Simply deleting the "-i" in the reboot command worked for me.  As per the MAN pages this option has to do with shutting down network shares and is not necessary since the kernel will perform this task.

I only had the problem during reboot but for those having this issue with shutdown there is a similar option on the halt command in the etc/init.d/halt file.  I have not tried this second fix.

Good luck to everyone with this troublesome problem.

---

### Post by roadmouse on 2008-10-16
I had the same problems. And replacing Network Manager with Wicd didn't work for me.

It turned out to be a problem with acpi in my case, not network manager.
I found the solution here:

[http://ubuntuforums.org/showthread.php?t=710131]("http://ubuntuforums.org/showthread.php?t=710131")

Replacing Network Manager with Wicd did however get rid of the  errors at shutdown, but it still wouldn't power off.

---

### Post by theDaveTheRave on 2008-10-18
Hi guys,

I reckon this is the most interesting thread I have so far come across!

I'm having a very strange shutdown issue.

I get no error messages, and run straight to the progress bar, as I would expect. however I then find that the screen doesn't allways die, and the power light stays on.

This is a highly intermittent fault, and reading what you guys have said I wonder it if is also related?

Anyway, next time I get this error I'll make a point of grabbing the dmesg to a file to see if there is anythin interesting in that, but I don't know what to look for?

Either way I have tried what Greg.T says about changing the boot / shutdown / restart scripts, but I don't see why removing the comments and then re-inserting them is going to actively change anything? :-k
if these comments really are the issue, it would seem like a simply <update> to change them, esecially as you have seen this a fair few months back and it is now mid october!

anyway I'm going to try this change to see if it solves my issue, admitedly I should probably wait for it to happen again, grab the dmesg and then do the change.... but it is a bit late for that now!:oops:

David

---

### Post by theDaveTheRave on 2008-10-29
Hello Again all,

After trying the solution suggested by GregT I can say that this worked fine, for a time!

The problem for me has now returned! most strange.

I can confirm however that doing a <sudo shutdown -h now> from the command line will make my pc shutdown just fine?

Personally I'm not finding Hardy particularly buggy and I am very happy with it.

However I think that due to the number of "bugs" like this that have been reported maybe they shouldn't have classed Hardy as the current LTS version - I admit to allways waiting 6 months or so after the release of a new version, just to allow the worst of the problems to be sorted, however this is supposed to be the LTS version. In my mind this means that the bugs should only be "minor" and an issue with my laptop not shuting down correctly is rather anoying (as this drains the battery!).

anway my simple fix of doing the shutdown from the CLI is fine for me, but I wouldn't ask my mum to have to do this every time!

Dave

---

### Post by shaun36 on 2008-11-23
I started receiving the same error messages at shutdown yesterday after disabling a disused modem port via my BIOS. Today I have enabled/disabled the port a number of times and in my case that is definitely the cause of the error messages. I don't know if this is useful or just adds to the confusion. Shaun

---

### Post by neophyte_of_linux on 2009-08-25
Hi everyone! My first post ever!  I'm a "noob" with Ubuntu Linux (or is it GNU Ubuntu Linux?).  I was "o.k." monkeying with basic settings on WinXP to make it run better or more secure (ha ha right). But I underestimated how "technical" linux would be - that said with my limited computer skills I managed to install Hardy Heron AND over the course of a months tinkering got almost trouble free multi-media functioning!  :)

So the only "issue" I've had since install is exactly the shutdown messages on the first post.  My computer shuts down or restarts fairly speedily - no hang ups - just the messages.......which initially had me concerned.

Well I'm glad I searched first, instead of posting, 'cause I found this thread.  I tried the Login "..." mods, and deselecting roaming (which actually made the shutdown worse -  slow/hang w/messages).  The problem message codes won't go away.

I just decided to leave it be.  It doesn't bother me if its not harming my system. Is this a sensible decision?  Or will problems accumulate?

---

### Post by JKyleOKC on 2010-06-04
> **Xiong Chiamiov said:**
> I'm can't help you with that one, since I don't use GNOME, but I know that [this]("http://ubuntuforums.org/showthread.php?t=772733&page=4#36") fix worked for me.I had the NetworkManager error messages on all my machines ever since installing Hardy LTS, and none of the other fixes suggested in this thread had any effect. Since all my systems are desktops, I decided to try the linked idea to disable Network Manager completely.

It worked perfectly, and in addition my net response seems to be a bit faster as well. Makes me wonder why Canonical doesn't automatically disable NetworkManager for desktop installations...

---


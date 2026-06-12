---
title: "T20 Feisty Great Success Story"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by GaryH on 2007-04-16
Hello Everybody,
So all I did was burn a CD with Feisty, install it on my T20, follow the instructions pointed to by  [http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20")
and everything worked, video, sound, wireless, USB, the whole enchilada!  Feisty is a grand triumph. My hat is off to the Ubuntu team.
[INDENT][/INDENT]:guitar:
For reference, the wireless is WG511T.

Only one ever so tiny glitch is present. The power doesn't shut off automatically at the end of the shut down sequence. The power button needs to be pressed and held for about one second to complete the sequence. Does anybody out there have a fix for this ever so small problem?

Peace,
GaryH

---

### Post by mattotoole on 2007-04-17
Great to hear it!  I'm still running Breezy because neither Dapper or Edgy will work with my T20.

Does your sound recording work?  Can you use VOIP?  Is your wireless working with WEP or WPA?

I ran the beta CD last night.  I had to use the VESA video setting, which seemed fine.  I got my wireless working (the new applet is neat) but not without some fiddling.  I'm not exactly sure what I did, but here's a basic rundown:

At first the new wireless applet didn't appear, and there was no connection.  So I opened the old style networking applet, and created a connection with a known-good ESSID and password.  After saving that the new wireless applet started, the connection worked, and I could see all the other connections too.  I haven't tested WEP (my card doesn't support WPA anyway).

With all versions of Ubuntu I've had the same problem with the machine not powering off.  Sometimes it works and sometimes it doesn't, and it seems completely random.  

I probably will install Feisty, but before investing my time I'd like to know if this other stuff will work.  Otherwise I'll probably buy a new laptop where it's certain.

---

### Post by blamecanada on 2007-04-17
I'm still using "network-manager", but feisty is supposed to add somthing else to help this.

---

### Post by GaryH on 2007-04-17
Hi mattotoole,
I didn't test sound recording, VoIP, WEP, or WPA. I always use public hotspots. What's involved in testing VoIP, and sound recording? What applications are to be run and what hardware is needed? I'm an EE and have access to some hardware. I guess I could just run a cable from my wife's audio output on her laptop and feed it into my audio input jack and try out the recording. Which application should I run? Maybe I could check out WEP and WPA at a computer store. Do I need a special phone to checkout VoIP? What application are you using for VoIP? Why buy a new laptop if it isn't necessary?

---

### Post by mattotoole on 2007-04-17
> **GaryH said:**
> Hi mattotoole,
I didn't test sound recording, VoIP, WEP, or WPA. I always use public hotspots. What's involved in testing VoIP, and sound recording? What applications are to be run and what hardware is needed? I'm an EE and have access to some hardware. I guess I could just run a cable from my wife's audio output on her laptop and feed it into my audio input jack and try out the recording. Which application should I run? Maybe I could check out WEP and WPA at a computer store. Do I need a special phone to checkout VoIP? What application are you using for VoIP? Why buy a new laptop if it isn't necessary?

Thanks for your willingness to test!  

To test sound recording, you can use Audacity, a sound recording app.  There may be simpler ones but I'm not familiar with them.  All you have to do is try to record a .wav file or something, say "hello" into the microphone and play it back.  Try your built-in mic (the two little holes near the cursor keys), and also a plug-in mic (jack on the left side of your T20, next to the headphone jack).

To test VOIP, just use Skype, Gizmo, Ekiga, or any other VOIP software, and see if you can make and receive a call to any normal phone.  This depends on the mic and speakers working, and/or headphones w/mic if you use those.  

Even public hotspots occasionally use WEP/WPA, to control access somewhat.  So it's worth checking.  Plus those of us who do use it would appreciate your testing!

I'll test some of this myself when I have time -- not this week.

Thanks again!

---

### Post by GaryH on 2007-04-17
**On going T20 and Feisty Test Results**:popcorn: 

[LIST=1]
[*]The power doesn't shut off automatically at the end of the shut down sequence. The power button needs to be pressed and held for about one second to complete the sequence. Does anybody out there have a fix for this ever so small problem?
[*]After tinkering with the mixer, the internal microphone worked fine either playing through the internal speakers or recording with Audacity. It was necessary to mute the microphone because of the external speaker microphone feedback loop. I used alsamixer as my "tinkering" tool to: 
[LIST=1]
[*]Select microphone 1
[*]Enable capture for mic, adc, and capture.
[/LIST]
[*]Increasing the volume with the T20 built-in volume control un-mutes the microphone and may start a feedback loop and scare the @#$%! out of you. Now that's a bug! 
[*]Now that the microphone works, all the hardware elements of a softphone are in place. I launched Ekiga, setup an account, and made my first softcall ever. It appears free calls are restricted to be from PC to PC. PC to phone incurs a charge.  Anybody out there know of a free service which offers PC to phone?
[*]The wireless manager seems to be a little buggy when using it at low signal, public hotspots. For some reason it always asks me for a password even if one it isn't required. I set it to manual, no roaming and now use the command line to connect as shown in the following. Note that my wireless port is named is ath0 and MAC is the 6 byte MAC address learned from running iwlist.
[LIST=1]
[*]sudo ifconfig ath0 up
[*]sudo iwlist ath0 scanning
[*]sudo iwconfig ath0 ap MAC
[*]sudo sudo dhclient ath0
[/LIST]
if I return to the same hotspot, all I have to do is re-run sudo dhclient ath0. My wireless system appears to remember the MAC address between power cycles.
[*]The power shutoff problem mentioned above was solved by adding acpi=force and pci=noacpi to the default options in the grub menu.lst as shown in **bold** below:
[INDENT]## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
**# defoptions=acpi=force pci=noacpi**[/INDENT]
I removed the splash and quiet options because I prefer seeing the boot log to the progress bar. Don't forget to run update-grub after menu.lst is modified. [COLOR="Red"]**Please double check your work.  A mistake may make your system unbootable.**[/COLOR]
[*]Now the LCD screen intensity is full bright after a power cycle. Before the shut off fix, the intensity was preserved between cycles. It appears the shut off fix introduced a bug. The bright dark buttons still function as before with an added benefit. Now a nifty icon is displayed during adjustment.
[*]Neither suspend nor hibernate work.
[*]If your not happy with the speed of your T20 Feisty Fawn please check out the following links for the excruciating details of a whole weekend of experimentation. Don't worry about doing everything I did. Most of the stuff didn't do much or was unstable. The real speed boost came from adjusting OpenOffice.org Word Processor options, converting over to Swiftfox, and configuring gnome for wireframe drag and resize. Good luck.
[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=425411](http://ubuntuforums.org/showthread.php?t=425411)
[*][http://ubuntuforums.org/showthread.php?t=427263](http://ubuntuforums.org/showthread.php?t=427263)
[/LIST]
[/LIST]



more to come...

Hope this helps T20 users everywhere!

Peace

---

### Post by jglen490 on 2007-04-17
Congratulations!!

I love my old T20 and am currently running Kubuntu 6.06 with no problems, other than the usual cast of characters.  Wifi was a pain, but after setting up ndiswrapper and blacklisting bcm43xx, and finding the right GUI wlan management tool, even that is slick.

I would hate trying a new distro so soon, because Dapper works so well for me, but Feisty sounds most interesting.

---

### Post by truck38chev on 2007-04-18
Has anyone tried to use voice in IM environment (gaim or aMSN)? 
If so how much success and what programes or files did you use.
Tony

---

### Post by GaryH on 2007-05-03
Hi Everybody,

I added links to Feisty Speed Up test results. :guitar: 

Peace,
GaryH

---

### Post by linuxmangr on 2007-05-15
I don't know if is work but you can to try my solution about not automatic shutdown , I test it on Desktop but I think is work on Laptop 
**[http://ubuntuforums.org/showpost.php?p=2662647&postcount=29]("http://ubuntuforums.org/showpost.php?p=2662647&postcount=29")**

---

### Post by goodmachine on 2007-05-20
seeing that you've had such success I decided to install ubuntu on my t20. Unfortunately for me I'm having trouble. The installation went well but I can't get it to boot, it starts fine hits the splash screen but stops on an all black screen after that. I'm at aloss for what to do, I'm definately a newbie and haven't come across a similar post, though I may have missed it. I'll keep looking but any help would be appreciated.

It's a T20 type: 2647-86U

---

### Post by GaryH on 2007-05-22
Sorry to hear about your problem goodmachine.  I had the same problem too. Most likely you did nothing wrong. Check out the link mentioned earlier in this thread: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20) especially step 2.1.

>  Blank Screen when booting Live CD

There is an issue with the Savage driver which makes the initial boot into X hang.

1. Hit F6 on the boot menu, delete "quiet splash" from the boot parameter line, and add "break=bottom".

2. After a while you will get a prompt (initramfs), type "chroot /root nano -w /etc/X11/xorg.conf".

3. Find your video card, and change driver "savage" to "vesa".

4. Save (ctrl+w), exit nano (ctrl+x), then press ctrl+d.

5. After that the live cd will work 

Good luck!

Peace,
GaryH

---

### Post by GaryH on 2007-05-22
Thanks for the tip econlab. Earlier in this thread a fix for the power shutdown problem was mentioned.
> 
was solved by adding acpi=force and pci=noacpi to the default options in the grub menu.lst as shown in bold below:

    ## additional options to use with the default boot option, but not with the
    ## alternatives
    ## e.g. defoptions=vga=791 resume=/dev/hda5
    # defoptions=acpi=force pci=noacpi

Thanks for the tip none-the-less.

Peace,
GaryH

---

### Post by crux19 on 2007-06-22
figured I'd keep the post.  I wasn't using the alternate CD.  I'll give that a try first.  Thanks

Hello,
I'm in the process of installing 7.04 on a T20.  I am following the instructions linked from this post:

There is an issue with the Savage driver which makes the initial boot into X hang.

1. Hit F6 on the boot menu, delete "quiet splash" from the boot parameter line, and add "break=bottom".

2. After a while you will get a prompt (initramfs), type "chroot /root nano -w /etc/X11/xorg.conf".

3. Find your video card, and change driver "savage" to "vesa".

4. Save (ctrl+w), exit nano (ctrl+x), then press ctrl+d.

5. After that the live cd will work 

I got through step 1 and am watching the text scroll through for boot up.  For some reason, it's hung at squashfs: version 3.2-r2... and has hung for about 15 minutes so far with no command prompt issued as mentioned above.  

Do I have to wait longer?  Am I missing something?

Thanks!

---


---
title: "How to recover from the great update pukeage for noobs :)"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Jim March on 2009-09-16
OK, I'll take it step by step.  It's not actually that bad to fix, now that the updates work.

But first, to the tune of "American Pie":

> A long, long time ago
Just last night in fact,
How my compiz desktop made me smile
And I knew if I had my way
That I could make Steve Balmer pray
And, maybe, he'd go FOSS, for just a while.
But today's update made me freak
As X would die with a horrid shriek
Bad news on the desktop;
My computer was a doorstop
I couldn't figure out what died
Or why my graphics card felt fried,
As if the update process lied,
The day Ubuuuuuuuuntu died.
So bye, bye to my work for the day,
Tried some hashes and some thrashes
but the boot was just nay
And ubuntuforum was all choked up and gray
singing "this has gotta be the day Karmic died"


Ahem.  Yeah.  On to business.

This is what worked for me, gleaned from various pieces of the long threads.  I'm going to put it into some detail here and clean up the various bits.

Applies to 32bit and 64bit.

Step one: find a real honest-to-god Ethernet connection.  No WiFi, no cellmodem, unless you know how to config one at the command line.  But if you knew that you wouldn't be reading this so never mind.

2) Reboot, using your last good kernel (probably -10) in RECOVERY MODE.

3) If you're doing whole-disk-encryption, put your password in.

4) At the menu, pick "netroot".

5) At the command line, do:

**ping [www.google.com](www.google.com)**

...and make sure you're online (you'll see responses back).  If not, sucks to be you, you probably need to manually configure a static address or something.  Assuming you have a basic Internet connection...

6) Next, do:

**apt-get update**

Make sure that runs right.  Note that you're already root, sudo isn't needed.

7) Do:

**apt-get upgrade**

Make sure it runs.  IF it says "holding back" *anything* at the end of that run, do:

**apt-get dist-upgrade**

8) At this point restart it and see where you're at.  Decent chance you're 100% back.  If not, two possibilities:

a) You're in some Godforsaken backwater like Mumbasa or London or something and your local server ain't updated yet.  Wait four hours, try again OR...

b) At the same time I was doing the above at the root prompt I tried swapping KDM for GDM - and on reboot everything blew up for reasons I still have no clue over.  So I got back to recovery mode, netroot prompt, did:

[B]apt-get install kdm kubuntu-desktop
[/B]
...and on reboot everything was fine.  It's possible something is still hosed in GDM.  Good news is, even using the KDE startup manager you can still pick a Gnome (or whatever else you're into) session.  Again: I don't know what this was about, but...this worked for me.  M'kay?

OH yeah. One more thing. I use an Intel video card.  If you're on AMD or NVidia with proprietary drivers, just for grins I would suggest going into the "hardware manager" and make sure everything is OK with proprietary drivers.

If you need to fix this with NO Internet connection at all on the broke machine...hmmm, it's probably possible to grab the latest .DEBs for upstart and initscripts on another machine, copy 'em to a CD or something and force-install 'em manually.  Let's see, the .DEBs are at:

64bit:

[https://launchpad.net/ubuntu/karmic/amd64/initscripts](https://launchpad.net/ubuntu/karmic/amd64/initscripts)
[https://launchpad.net/ubuntu/karmic/amd64/upstart](https://launchpad.net/ubuntu/karmic/amd64/upstart)

32bit:

[https://launchpad.net/ubuntu/karmic/i386/initscripts](https://launchpad.net/ubuntu/karmic/i386/initscripts)
[https://launchpad.net/ubuntu/karmic/i386/upstart](https://launchpad.net/ubuntu/karmic/i386/upstart)

Grab the latest version of each, copy them to some sort of readable media, get them onto the machine that needs fixin', do:

dpkg -i [packagenamewithoutbrackets.deb] --force

...to install each.  If there's dependencies, dayum, you'll have to find and download those too.  Lot of work but it should be possible.

Good luck...

Jim March

---

### Post by ranch hand on 2009-09-16
Well.  I for one am happy to see someone having FUN.

The info looks good too.  I never though of grabbing the debs.  What a great idea.  If you run a search for the package you should find a page of details of the package, including dependencies and links to them.

I am here to learn and I chrooted in and updated and upgraded.  FUN.

---

### Post by slakkie on 2009-09-16
I like the tune :D Actually, this post made me grin. I wish I could write guides with so much humor in it.. hehehe

---

### Post by Jim March on 2009-09-16
This was written to avoid chroot because those of us doing whole disk encryption via the alternate install CDs (and LVMs) can't chroot - we can't get a LiveCD to talk to our disks at all.

Or at least, I couldn't with a Karmic Alpha4 LiveCD, even after installing the crypto software mentioned in the first error message.  Maybe the Alpha5 CD can, I dunno.  Anyways.  This plan avoids chroot from a LiveCD.

---

### Post by TDK800 on 2009-09-16
I am able to go to kernel recovery mode, but when entering the full disk decryption password it says:

Unlocking the disk /dev/disk/by-uuid/b7w8.... (sda1_crypt)
Enter passphrase:
key slot 0 unlocked.
Command sucessful.
File descriptor 3 left open
2 logival volume(s) in volume group "x" now active
cryptsetup: unknown fstype, bad password or options?
Command failed: Device busy
Unlocking the disk /dev/disk/by-uuid/b7w8.... (sda1_crypt)
Enter passphrase: Command failed: Device already exists

And then drops me to the builtin root, may be something to do with the new mountall package. Anyone had luck accessing fully encrypted disks with Live CD? Or any other suggestions?

---

### Post by Jim March on 2009-09-16
Ow.  That's not good.

In my case, I've been able to unlock the disk when booting from the hard disk, but never with LiveCD so far.

The furthest I got was to do **sudo apt-get install cryptsetup** on the LiveCD, then try unlocking the disk at the GUI.  It then takes the first password, but asks for a second password.  I've tried feeding the second password everything I can think of with no joy.

If I was in your boat, I'd strongly consider downloading the latest daily build LiveCD, do **sudo apt-get install cryptsetup** as soon as I had a GUI+networking and could pull up a terminal window, and then try accessing the encrypted disk.  If you can do that, great, do chroot to get into it deep enough to do updates directly to it.

It's possible the encrypted disk access from LiveCD is broken in Alpha4 but fixed later.

---

### Post by TDK800 on 2009-09-16
Thanks, will give it a try with the latest LiveCD build and post results in few hours.

How do I do the chroot to get updates to the disk?

---

### Post by Jim March on 2009-09-16
[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)

And that reminds me of something else: as long as the other Linux distro's LiveCD you're using supports Ext4 (if you went there!) and encrypted volumes, it's possible that just maybe a Knoppix or other LiveCD might work better than an Ubuntu LiveCD!!!

Hrm....yeah, that's food for thought, ain't it, if the latest Ubuntu LiveCDs puke on encrypted file systems?

Huh.  Wait, let's ponder some more.  Jaunty supports Ext4 too.  So a Jaunty LiveCD might be worth a try.

I just don't have time right now to try these concepts out but...at some point, I *do* want a LiveCD that can access my encrypted drives (with passwords of course).

---

### Post by TDK800 on 2009-09-16
Latest cryptsetup was installed on LiveCD.

Followed this to mount fully encrypted drive:
[http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html)

modprobe dm-mod failed with message : FATAL: Module dm_mod not found.

Which is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/343147](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/343147)

And probably the reason for this mount error:
sudo mount /dev/x/root /mnt/fcroot -o ro,user
mount: you must specify the filesystem type


Tried specifying lvm and lvm2 too:
sudo mount -t lvm2 /dev/x/root /mnt/fcroot -o ro,user
mount: unknown filesystem type 'lvm2'

---

### Post by TDK800 on 2009-09-16
When booting from disk to recovery kernel and entering incorrect password it gives different error, so the reason for not loading the partition must be related to the "unknown fstype" part of the error. 

May have been caused by doing fschk due to the errors it started giving with the latest updates and the fschk then crashing, and messing up the filesystem.

Doing a clean install again. Thanks for the help.

---

### Post by fazza on 2009-09-16
I.. would love to do this, but I don't know how to boot into recovery mode with grub 2... any ideas please?

---

### Post by VMC on 2009-09-16
> **fazza said:**
> I.. would love to do this, but I don't know how to boot into recovery mode with grub 2... any ideas please?

If you get grub2 menu, then just "e" for edit. Then its a simple matter to add "single" (without quotes) to the end of the kernel line. Then Ctrl+x to boot into recovery mode.

A caveat though. Last night with all the update fiasco it brought me to am X screen?!

---

### Post by EzraReeves on 2009-09-16
Updating doesn't fix anything for me ](*,)

---

### Post by grandtoubab on 2009-09-16
> **EzraReeves said:**
> Updating doesn't fix anything for me ](*,)
with 2.6.31.10 and GNOME 2.27.92, Now I have only the loggin screen for tty1.:confused:
As we say here best is ennemy of good!:lolflag:

Once again this save me:
1)log to your account in tty1
2)sudo start dbus
3)sudo start hal
4)sudo start network-manager (i am on ADSL via ethernet)
5)sudo start gdm

And I can use my desktop but if I reboot... pim...pam...poum have to go back in item 1:guitar:):P

---

### Post by fazza on 2009-09-16
> **VMC said:**
> If you get grub2 menu, then just "e" for edit. Then its a simple matter to add "single" (without quotes) to the end of the kernel line. Then Ctrl+x to boot into recovery mode.

Yeah but I can't get into the menu... what to I press to drop into the menu?

---

### Post by Jim March on 2009-09-16
> Updating doesn't fix anything for me

Did you try:

sudo apt-get dist-upgrade

?

That's what I had to do to get the last push of stuff.

---

### Post by VMC on 2009-09-16
> **fazza said:**
> Yeah but I can't get into the menu... what to I press to drop into the menu?

You are presented with a grub menu but you can't edit or get to the command prompt? What exactly do you see after you turn on your pc?

---

### Post by Jim March on 2009-09-16
Some time ago I had to edit my grub config to allow access to the menu.

If you can't get to the grub menu AND you can't use chroot because you've got an encrypted disk, you're kinda screwed here.  Only choices left are reformat/reinstall, or find a different LiveCD that can deal with the encryption (by accepting the password - "cracking it" ain't gonna happen).

---

### Post by fazza on 2009-09-16
> **VMC said:**
> You are presented with a grub menu but you can't edit or get to the command prompt? What exactly do you see after you turn on your pc?

I have grub 2, which doesn't present you with a menu OR tell you what  to press to see it (by default, at least). So I can't even view the menu. :S

---

### Post by VMC on 2009-09-16
> **fazza said:**
> I have grub 2, which doesn't present you with a menu OR tell you what  to press to see it (by default, at least). So I can't even view the menu. :S

I think if you hold down the shift key when grub boots it will help.

Go [**here**]("http://ubuntuforums.org/showthread.php?t=1195275") for some good information and some more links to help you.

---

### Post by fazza on 2009-09-16
Ah okay thanks :)

However I think I may have just fixed it...
going down for a reboot from my live disc, so I may not be back for a while.. :P

I managed to do updates from the live disc by mounting my root partition with ```
mount -o dev /dev/sda10 /media/disk
``` which allowed them to work.. when the partition is just mounted normally, it refuses to even run apt-get update O_o

anyway thanks :)

---

### Post by fazza on 2009-09-16
Um no that didn't work
I got into recovery mode through Grub though, thanks
When I was inside, I tried to run the winbind daemon, to see if it actually worked or not, and it does. HOWEVER: the program is called winbindd, but during bootup, when it says "Starting Winbind Daemon" or whatever it says, next to it, it only says winbind.
I was thinking perhaps, in the update, a bootup command was changed by accident, and now the necessary program isn't run?

Also, now I'm running the Live disc again, I thought I would try to find out what exactly winbind is by running it. But it's not installed. Does that mean it's not necessary? Can I uninstall it from my root system?

---

### Post by jlacroix on 2009-09-16
I think my box is borked beyond repair. It doesn't really matter to me because I have all of my files backed up in two other places so I may just reinstall Kubuntu. (None of my kernels, recovery mode or otherwise, works).

So I ask you guys this: If I grab the latest daily image, would I still have a problem updating or would it have been created after this problem?

---

### Post by Jim March on 2009-09-16
Ummm...let's see, the latest daily image SHOULD have the newest tweaks (which do work, which is why running updates works.

I don't think the "craptastic update" made it into a daily build.

You're actually just as safe installing from the latest Alpha CD and then doing an update, as updates work now.

---

### Post by zika on 2009-09-16
> **Jim March said:**
> Ummm...let's see, the latest daily image SHOULD have the newest tweaks (which do work, which is why running updates works.

I don't think the "craptastic update" made it into a daily build.

You're actually just as safe installing from the latest Alpha CD and then doing an update, as updates work now.
Beware that Daily LiveCD is not working properly, at least in my case ... It is burned OK, that is not the problem.

---

### Post by Jim March on 2009-09-16
Ah.  OK, no sweat, use the latest "official alpha".  #6 is due tomorrow ain't it?

---

### Post by KitchenKnif on 2009-09-16
hmm.
the thing that saved many 
"Once again this save me:
1)log to your account in tty1
2)sudo start dbus
3)sudo start hal
4)sudo start network-manager (i am on ADSL via ethernet)
5)sudo start gdm
"

doesn't work for me. when I try to start any of them, I get something along the lines of 'already running'... :-/

---

### Post by fazza on 2009-09-16
Sorry to be a pain and quote myself, but it's becoming a bit of a pain to rely on a live system... Could this be anything?

> **fazza said:**
> Um no that didn't work
I got into recovery mode through Grub though, thanks
When I was inside, I tried to run the winbind daemon, to see if it actually worked or not, and it does. HOWEVER: the program is called winbindd, but during bootup, when it says "Starting Winbind Daemon" or whatever it says, next to it, it only says winbind.
I was thinking perhaps, in the update, a bootup command was changed by accident, and now the necessary program isn't run?

Also, now I'm running the Live disc again, I thought I would try to find out what exactly winbind is by running it. But it's not installed. Does that mean it's not necessary? Can I uninstall it from my root system?

---

### Post by jlacroix on 2009-09-16
Thank you guys, I'll just reinstall later on today and see if that fixes it. I probably would have reinstalled anyway. Before this crash my PC would boot into X only 1 in 20 times so I'm hoping I can find a way to fix that...

---

### Post by AVakil on 2009-09-16
The first post in this thread was very helpful.  Thanks.  I am back up and running again.

---

### Post by Jim March on 2009-09-16
Glad to hear it.  I didn't invent any of this, I just tried to put all the various notes in one place.  Too many original contributors to credit easily.

Lyrics are all mine :).

---

### Post by VMC on 2009-09-16
I think the best advice is **not to panic** - which I did yesterday, and made things worse. 

I just relied on my main jaunty install to chroot into karmic and kept doing updates when I could. Eventually, I got past all the fsck, blinking cursors, freezes, and the like to a normal running karmic again today.

---

### Post by DarkReaper79 on 2009-09-16
Following this how-to worked for me. I had to do the dist-upgrade to make it work. What fun to deal with after a crappy day :P At lease now it works, Thanks!

---

### Post by Jim March on 2009-09-16
I forgot to mention "step zero" in my tale of getting my laptop under control.

Step zero:

1) Call landlady.

2) Explain that I just scored 3lb of salami at Costco, and ask if she wanted a chunk.

3) She did (and yeah, I mean actual salami, not "hide the salami"...sheesh...)

4) "Cool, I'll be right over.  Hey, while I'm there, you mind if I plug straight into your router, you know, that UFO-lookin' thing (Apple) so I can fix my computer, 'cuz my WiFi is broke?  (Along with X and lots more, but she wouldn't know what X-windows was if it bit her in the butt...)

So yeah.  I ended up scoring hardwire access for 3/4lb of salami.

:guitar:

---

### Post by blakamin on 2009-09-17
> **Jim March said:**
> 

Lyrics are all mine :).

And they are fantastic!!!! You made my day after sitting there typing "sudo apt-get update" and.... actually I lie, I just used the up arrow over and over again for 4 hours. And the occasional reboot for luck.

:guitar:

---

### Post by Jim March on 2009-09-17
When stuff craps out like this, you just gotta laugh at some point.

And I'm running on the ragged edge: I own a grand total of ONE computer, period...with the whole disk set up Karmic Ext4 encrypted.

---

### Post by stinger30au on 2009-09-17
Jim March wrote:

OK, I'll take it step by step.  It's not actually that bad to fix, now that the updates work.

But first, to the tune of "American Pie":

 	Quote:
 	 	 		 			 				A long, long time ago
Just last night in fact,
How my compiz desktop made me smile
And I knew if I had my way
That I could make Steve Balmer pray
And, maybe, he'd go FOSS, for just a while.
But today's update made me freak
As X would die with a horrid shriek
Bad news on the desktop;
My computer was a doorstop
I couldn't figure out what died
Or why my graphics card felt fried,
As if the update process lied,
The day Ubuuuuuuuuntu died.
So bye, bye to my work for the day,
Tried some hashes and some thrashes
but the boot was just nay
And ubuntuforum was all choked up and gray
singing "this has gotta be the day Karmic died" 			 		




Jim, mate this is a magic 

love ya style

---

### Post by Jim March on 2009-09-17
You should have seen me cuttin'n'pastin' the first chunk of the original lyrics I googled for, making space below each line for my replacement line, and then counting syllables on my fingers to get it right :).

Weird Al doesn't have THAT hard a job. 
:guitar:
:lolflag:

---

### Post by luvr on 2009-09-21
> **Jim March said:**
> If you need to fix this with NO Internet connection at all on the broke machine...hmmm, it's probably possible to grab the latest .DEBs for upstart and initscripts on another machine, copy 'em to a CD or something and force-install 'em manually.

Something occurred to me while reading this. Don't know  if this makes sense in any practical way, but: Assume that you installed the updated packages to another machine, which **did** have internet access, first.

Couldn't you, then, copy them from the APT cache on that machine, and bring them over to this computer that doesn't have internet access? That would take care about any dependencies, since these would all have been resolved in said APT cache.

---


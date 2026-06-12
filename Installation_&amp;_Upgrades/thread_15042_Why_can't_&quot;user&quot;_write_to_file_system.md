---
title: "Why can't &quot;user&quot; write to file system?"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by bigkahuna on 2005-02-11
I've installed Warty and set up one "user" since this is my personal system.  Something I don't understand about Ubuntu though:  why can't a "user" write to the "filesystem"?   Doesn't that keep the user from being able to save any work at all?

How do I permanently change the "user" to be able to write to the "filesystem"?

Thanks

---

### Post by az on 2005-02-11
"why can't a "user" write to the "filesystem"? Doesn't that keep the user from being able to save any work at all?"

That would be stupid.  You can write to your home directory.  You put all your user stuff there.  Your user does not need to write to anywhere else.


How do I permanently change the "user" to be able to write to the "filesystem"?

It is like eating in your bathroom.  It is just wrong.  But if you insist, run your system as root, or install windows.

Do not run your system as root.  This is not a good idea.  Root should only do administrative things.

---

### Post by Sgood1971 on 2005-02-11
[QUOTE=azz]It is like eating in your bathroom.  It is just wrong.  But if you insist, run your system as root, or install windows.[/QUOTE]

Funny, but true. For the rare times you need to write to anything to /home/username there is sudo. Your /home directory is the place to store all your goodies.  The inability for a regular user to write over any critical system files is a good thing. That's why in Windows a virus can destroy so much, it runs as a regular user with full admin rights so it can delete/replace/modify any system file it wants to.

---

### Post by bigkahuna on 2005-02-11
... aaahh, "user" can write to his "home" directory.  That makes sense.

As you have already guessed, yeah, I'm a Linux newbie and I'm just starting to figure things out.  I've borrowed a couple books on Linux and have read a ton of pages on the net, but finding answers to a "simple" question like this is often hard to find.  It didn't make any sense that Ubuntu would require all file writing to be done as root, so that's why I asked the question.  Thanks for your fast answers!

I ran into this problem when I wanted to install an app (Blender) on my freshly installed Ubuntu Warty.  I expected it to be difficult, but it really wasn't.  I wasn't able to access the "file system" to install the app so I logged in as root.   Using "sudo" means I'd have to do everything in a terminal window, which I'm not real comfortable with yet.  So I changed the "log in screen" settings to allow root to login to Gnome and installed that way.

Is this the normal way of installing an appication, or should I just install to my "user" home directory?  I'm the only user on this system.

Thanks,

Paul

P.S. - my modem doesn't work in Linux (winmodem) so I'm downloading new app's through XP to a Windoze partition, then copying it to the Linux partition after I've rebooted Ubuntu.

---

### Post by az on 2005-02-11
What is your modem?

There are drivers for some.

---

### Post by k.ODOMA on 2005-02-11
[QUOTE=bigkahuna]So I changed the "log in screen" settings to allow root to login to Gnome and installed that way.[/QUOTE]

You *can* install software this way, but it's really not a good idea. You are able to do anything with sudo that you can do when you log in as root, but with sudo, it's just a hair more inconvenient and therefore a stronger reminder that you have the ability to completely bork your system if you want to.

When you log in as root it's real easy to forget what account you are... until you've erased some critical partition.

---

### Post by bigkahuna on 2005-02-11
[QUOTE=azz]What is your modem?

There are drivers for some.[/QUOTE]

It's a Conexant HSF softmodem.  I've seen that Linuxant has a driver for it, but looks like installing it is a bit beyond my skill level.  There isn't a binary for Ubuntu, so I'd have to compile my own...  I'm not there yet.

---

### Post by bigkahuna on 2005-02-11
[QUOTE=k.ODOMA]... When you log in as root it's real easy to forget what account you are... until you've erased some critical partition.[/QUOTE]

OK, I'll remember that.  I just tried copying files to the user's "home" folder for the first time... easy enough!

I'm a Windoze / DOS / Mac user since the early 80's...  XP and M$oft have really p*ssed me off, so I'm learning Linux as fast as my poor feeble brain can handle it  :grin: 

Thanks

---

### Post by Sgood1971 on 2005-02-11
[QUOTE=bigkahuna]OK, I'll remember that.  I just tried copying files to the user's "home" folder for the first time... easy enough!

I'm a Windoze / DOS / Mac user since the early 80's...  XP and M$oft have really p*ssed me off, so I'm learning Linux as fast as my poor feeble brain can handle it  :grin: 

Thanks[/QUOTE]
 You can always use synaptic to install apps if you are not comfortable in cli, but even in cli it's usually as easy as....

'sudo apt-get install <packagename>' and wait for it to finish. When you launch synaptic it will ask for your root password so that program runs with root rights, but you still do not have them.

---

### Post by bigkahuna on 2005-02-11
[QUOTE=Sgood1971]You can always use synaptic to install apps if you are not comfortable in cli, but even in cli it's usually as easy as....[/QUOTE]

... ahhh, but I'd need an internet connection to use synaptic, right?  And right now I don't have an internet connection through Linux.  I've got one of those darn Winmodems in my Sony Vaio notebook.  I'm holding off on buying a PCMCIA modem because I'm hoping I'll be able to afford a DSL connection and modem...

But for now I'm stuck with my 56 kb winmodem and downloading through Windoze XP.

Incidently, for any fellow "former XP" users out there:

I just finished doing a clean install of Windows XP SP2 on my notebook.  My system has been extremely unreliable as of late and I've been wanting to do this for weeks now.  So far nothing is installed but the OS and whatever software Sony put on their "recovery CD's".  Guess what WinXP did no less than 5 minutes after a clean install?  Yup, you guessed it, it locked up solid...  gotta luv that M$oft technology  :wink: 

Yeah, I can't wait to get Ubuntu up and running 100%...

---

### Post by grj on 2005-02-11
You may also install install applications from CDs. Your Ubuntu CD has some apps on it and if you can get copies of Debian CDs you can get many apps.

To add CDs to your repositories:

put a CD into your drive
open a terminal window
type sudo su
when prompted for a password type your users password
type apt-cdrom add

and follow an instruction that may apper.

Then you can install apps from the CDs until you can solve your modem issues.

---

### Post by az on 2005-02-11
Insofar as your modem, you are unlucky.  You will have to pay linuxant for their driver and you only will get a year's support, or so.  That means that in a year, if you are using a different kernel, you will not be able to compile the driver for it without paying.

You are far better off to buy a better modem.

---

### Post by bigkahuna on 2005-02-11
[QUOTE=azz]... You are far better off to buy a better modem.[/QUOTE]

Yup, my thoughts exactly, thanks for confirming this for me.

---

### Post by bigkahuna on 2005-02-11
[QUOTE=grj]You may also install install applications from CDs. Your Ubuntu CD has some apps on it and if you can get copies of Debian CDs you can get many apps.... [/QUOTE]

Oh?  I didn't realize the Ubuntu install CD had more software, I'll have to check that out!

Thanks also for confirming one other bit of information I was wondering:  from your post I'm guessing that any Debian binary will work with my Ubuntu Warty install...  that's great!  I've seen a number of apps I want to download, and wondered which binary will work... know I know!

Thanks!

---


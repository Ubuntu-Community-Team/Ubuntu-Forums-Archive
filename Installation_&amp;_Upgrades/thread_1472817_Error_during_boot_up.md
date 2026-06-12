---
title: "Error during boot up"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by RMcD94 on 2010-05-04
I attempted to upgrade to the new release today, and I left it to download packages and what not. Came back, and turned it off.

Haven't been on it at all since then.

Turned it on moments ago to see once it gets to the Kubunto loading thing, it cuts to

Ubuntu 10.04 LTS RMcD94 ttyl

RMcD94 login:


So I tried RMcD94 and nothing for the login, with my password. Neither worked.

Password: 

Login Incorrect.

Turned it off, turned it on. Still happens.

So I decide to press esc during the kubuntu splash screen, and this appears:

WOW. Okayy that didn't happen last time.

Okay, says a lot of stuff. 

fsck from util-linux-ng 2.16  

That's the first line

Then something about clean, #/# files, #/# blocks in /dev/sda1

Then I get asked for my login again. Again incorrect.

Help?

Edit: Alright, I got my login, I had to take it out of capitals, forgot about that. But now it just tells me the date, and leaves me with a command line. Now what?

Edit 2: I'm really worried about my files. I don't have them backed up yet. I've been waiting to get some external storage to do so.

---

### Post by efflandt on 2010-05-05
If you are getting to a Linux command line on a full screen terminal after logging in, try typing **startx** and see what happens.  That should start whatever default X server and window manager.  If that does not work or the error is not apparent, look at /var/log/Xorg.0.log and see if that gives a clue.

You might also try **dmesg | less**, to see if that shows any errors.  Just hit the Q key to quit less.

---

### Post by RMcD94 on 2010-05-05
So I stuck in my old Ubuntu disk and booted from that. My files are there,  but the permission is locked for all of them. So I'm not allowed to copy them into my USB. Won't  let me change the permissions because I'm not the owner. Anyway for it ask me the username and password so I can change it?

Edit: Ha ha, ninja'd.

Edit 2: Okay, I can't get to the command line,. I tried to install it again. With sudo apt-get install kubuntu-desktop, however now it just comes up a weird gridded screen with Kubuntu in the middle. Annd then it messes around with all the pixels on the screen before turning completely black and doing zilch. 

When I press the Shut Down thing it goes to Kubuntu, with 5 dots underneath.

[IMG]http://4.bp.blogspot.com/_1PykOXo2c5I/S7KpNRBy9II/AAAAAAAAAKw/TV5b7dboNWk/s1600/kubuntu-plymouth.png[/IMG]

Like that.

I should have tried my Ubuntu disc before I tried doing that install thing.

None the less, my files are there. I just need to save them. (40 GB worth)

It's like that on start up, except as I said, gridded and slowly turns to black after going through every colour.

---

### Post by dino99 on 2010-05-05
unetbootin

---

### Post by RMcD94 on 2010-05-05
What?

---


---
title: "Can not log in to my system"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by Ubu_Fester on 2012-10-04
I was getting the following errors when I was using certain commands in terminal:

[HTML]  Gtk-WARNING **: Locale not supported by C library.
         Using the fallback 'C' locale.[/HTML]I found this link:

[http://askubuntu.com/questions/33025/locale-settings-are-not-right-how-can-i-reset-them](http://askubuntu.com/questions/33025/locale-settings-are-not-right-how-can-i-reset-them)
and performed the following commands:

[HTML]     sudo apt-get install language-pack-en-base
     sudo dpkg-reconfigure locales
     apt-get install --reinstall locales [/HTML][SIZE=3][COLOR=DarkRed]That seemed to fix the terminal issue, but when I reboot the system, I am now locked out of my username.  I can only log in as a guest!  Help!!!   [/COLOR][/SIZE]  :confused:

---

### Post by sigmatht on 2012-10-04
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Ubu_Fester on 2012-10-04
OK, I'll try that tonight.  Thx

---

### Post by Ubu_Fester on 2012-10-05
No, this did not work.  I also tried another approach using a live CD which did not work.

My problem appears to be different from the standard "lost my password".  I am getting a login window with three options:  My name, guest and other.  When I select my name from the list I then enter my password.  When I enter my password correctly, I get no error message and the system ends up not logging in.  It does nothing.  When I enter an incorrect password, I get a message saying so.  My only option is "guest".  But still it hits some infinite loop trying to go into mythtv - but can't -- because my guest account does not have permission to go into mythtv.

My current setup:
I'm running mythbuntu and for the last couple of weeks (after a clean install to 12.04) my system was setup to boot up, sign in automatically and enter the mythtv frontend.  Then, 2 days ago, I get into this situation.  This sucks. 

I did two things to my system prior to this issue happening.  
1) I tried to fix a "C library / locale" issue that occurred during some of my terminal sessions.  I used the commands in my first post to fix.
2) I installed remastersys.  With the intention of creating an iso of my fairly pristine system so that I won't have to go through the nightmare of reinstalling my setup.

Remastersys was a complete waste of time.  I spent two nights trying to get an iso, but with this software you don't know if you set something up wrong until after it crunches for 2 hours.

I love mythtv, but this linux world sucks.      :(

---

### Post by steeldriver on 2012-10-05
Can you login at a non-graphical virtual terminal (Ctrl-Alt-F1 and so on)? if so then the problem is likely something to do with your X session - either an Xauthority issue or maybe something in your profile that is preventing correct session startup

---

### Post by Ubu_Fester on 2012-10-05
[SIZE=3]**[COLOR=Red]I'm totally discouraged by this Linux box.  [/COLOR]**[/SIZE]:(

It's frustrating -- I try and get my answers from existing threads -- which led me to the two procedures that I did (noted in my previous post) -- HOWEVER, I'm convinced that one of those "fixes/improvements" actually caused my current situation.  It seems to be a gamble whenever I start typing "apt-get...."  I don't know what will break next....

Screw it.  I'm just going to wipe my disk and start over.  again.

---

### Post by darkod on 2012-10-05
It might be a stupid question but did you set your keyboard layout correctly during the original installation or didn't bother?

One of those commands you used mentioned locale settings and if you originaly typed your password with different locale, it might not type it correctly now especially if you used some special characters.

In any case, the procedure of resetting the password from recovery mode should work. Where exactly does it fails?

---

### Post by Ubu_Fester on 2012-10-05
Darko:  I believe my language package is fine.  Keyboard and everything should be regular U.S. English.  when I'm in a terminal, all the keys seem to be working fine.

I did perform a full clean install of the OS.  I was surprised to find that the same login problem exists.  Since my '/home' folder is in a separate volume and I didn't reformat that volume, the problem reappeared.


Steeldriver:  Thanks for your reply:

> Can you login at a non-graphical virtual terminal (Ctrl-Alt-F1 and so  on)? if so then the problem is likely something to do with your X  session - either an Xauthority issue or maybe something in your profile  that is preventing correct session startupYes, I can log in by pressing Ctrl-Alt-F1.  I can use basic unix commands, but would need more instruction on what to edit or delete.  (I'm not really a good VI editor user).

---

### Post by Ubu_Fester on 2012-10-05
Here is my login screen:

---

### Post by Ubu_Fester on 2012-10-05
OK, I'm getting closer

I was able to remove the file ~/.Xauthority.   Reboot -- but same results.  Few more attempts also didn't work, like investigating the lightdm logs as recommended from a post I saw.

From a "df" command I realized that my /home was full.  It wasn't a couple of days ago -- in fact it should only be about 30% full.  I then realized there was indeed some large files in my remastersys folder.  I deleted some of the key folders under remastersys, reboot, and now my system logs in automatically to an xfce interface.

Now I've got to rebuild the mythtv database. Hopefully my restore will go smooth.

---


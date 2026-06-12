---
title: "Plymouth Freeze Update"
date: 2010-02-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-02-12
I found a solution of sorts. I have the latest updates including Plymouth:

```
Package: plymouth
State: installed
Automatically installed: no
Version: 0.8.0~-10
```


It still froze ***until I removed the auto login***:
 "System > Administration > Login Screen" , from 
Log in automatically to 
show the screen for choosing who will log in

So if you have the automatically log in feature enabled, then disable it and see if the Plymouth now works.

I have re-booted over 12 times. Turned off pc then re-boot several more times. No more freeze.

Somehow the "Log in automatically" feature is messing up Plymouth.

---

### Post by ranch hand on 2010-02-12
Ah, that explains why mine work better.  I never use the auto login.

There is still a very fragile feel to booting though.

---

### Post by VMC on 2010-02-12
I created a bug report just to be on the safe side. Knowing there are several Plymouth bugs opened.

I want to make sure this scenario is fixed.

Launchpad Bug [#521175]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/521175")

---

### Post by ranch hand on 2010-02-12
Seeing your post and bug, I decided that it sounded like FUN.

I logged in.  Booted great.  Changed to auto login.  Won't boot.  Joined bug.

Now, as a side note.  I do not know the command to set/unset auto login.  Did it with the gui.

When I got in through recovery the gui will no longer "unlock".  I would like 2 things.

1>command to require password

2>the package to file a bug on for the login screen gui

---

### Post by VMC on 2010-02-12
> **ranch hand said:**
> Seeing your post and bug, I decided that it sounded like FUN.

I logged in.  Booted great.  Changed to auto login.  Won't boot.  Joined bug.

Now, as a side note.  I do not know the command to set/unset auto login.  Did it with the gui.

When I got in through recovery the gui will no longer "unlock".  I would like 2 things.

1>command to require password

2>the package to file a bug on for the login screen gui
Thanks for joining the bug, It will be interesting to see what duplicate if any is attached to it.

Your right. Once its frozen you have to chroot into the troubled partition and then issue a command to get login back. I never thought of that. 

OK, I found it:

```
gdmsetup
```

Try that to unlock your login features.

---

### Post by ranch hand on 2010-02-12
I will give it a whack.  I do not think it needs to be a chroot environment.  I can get to the desktop.

Just can't get there the right way.  If I boot to recovery and then log in (text) with "startx" I am in just fine.

---

### Post by VMC on 2010-02-12
> **ranch hand said:**
> I will give it a whack.  I do not think it needs to be a chroot environment.  I can get to the desktop.

Just can't get there the right way.  If I boot to recovery and then log in (text) with "startx" I am in just fine.

Ranch hand, you might want look at the bug report again.

 Steve Langasek has asked me to supply several outputs during a freeze. There's nothing I can do. Its frozen. 

I did supply the info during a normal boot. 

I wonder since you have been using ssh is it possible to login to your other machine when it freezes and use a terminal? I surly can't.

---

### Post by ranch hand on 2010-02-12
I might be able to do that from my wifes box.

I can't do it from what I run as the test platform is just a dual external enclosure with two 320Gb drives in it.  All my installs are on the same hardware.

I would have trouble doing it in that all I really know how to do with ssh is to connect and share stuf in the Home folder using the gui to connect.

If you know of a good tutorial on actually using ssh to do that kind of thing I would be glad to try and set it up and give it a whack.

---

### Post by VMC on 2010-02-12
> **ranch hand said:**
> I might be able to do that from my wifes box.

I can't do it from what I run as the test platform is just a dual external enclosure with two 320Gb drives in it.  All my installs are on the same hardware.

I would have trouble doing it in that all I really know how to do with ssh is to connect and share stuf in the Home folder using the gui to connect.

If you know of a good tutorial on actually using ssh to do that kind of thing I would be glad to try and set it up and give it a whack.

Thanks, but I think nothing will work. When it freezes, game over. Even if you could ssh into the box what good would that do. There is no activity. Even my monitor is off. Just the hard drive running.

My only hope is to chroot into the box from another os and dump some file content.

---

### Post by ranch hand on 2010-02-13
Just read the bug over again.

Boy, when you decide to freeze up your box you do not fool around.  Good job.  You are having more FUN than I am.

I do not see how I could get the answers he needs either.  Every symptom before the freeze is like your answers.  My freeze can be rebooted out of and I can boot in from recovery.  I also have a different card.

---

### Post by Ibidem on 2010-02-13
I don't know whether the processes would start, but you might try setting up a script to run automatically at login, with output redirected to log files:
```
cp /proc/fb ~/fb.log
#Or cat /proc/fb>~/fb.log
ps aw | grep X.*vt>~/awxvt.log
```That last command would be more troublesome:
```
sudo initctl list>~/initlist.log
```would require that you setup sudo to not ask for your password.
Then you'd be best to wait 5 minutes or so after boot and then shutdown and copy the files manually.
If you don't have any files there, it means it froze solid before running scripts.
Not quite sure which file to edit  to autorun these, but I know it can be done.

Ibidem

---

### Post by VMC on 2010-02-13
Ranch hand, Steve Langasek has asked if ssh will work. As I expected. 

If you can try it, that would be great. 

In the meantime I will research ssh and try to figure out how to run it. I seriously doubt ssh will work. There is no HD movement and no input after Plymouth freezes the system.

---

### Post by ranch hand on 2010-02-13
I am trying to learn to use ssh to do more than share files through the gui connection.  I have found this that may or may not be any good, at this point I wouldn't know.  It does have some major differences from other "expert" stuff I have found, none of which seemed to work at all.

[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)

---

### Post by sparker256 on 2010-02-14
Been following this thread and I am seeing the same thing with my daily live thumb drive. Have been seeing this for a week or more but was trying to figure out what the issue was. As the Live USB is set up to autologin it is giving the same symptoms. If I remove Plymouth it is usable again.

One symptom is if I go into terminal and press enter that will be a hard lock up. When this happens it is like the keyboard and mouse are not of any use. 

I will add myself to your bug and see if we can get this resolved as if I can see this on a live USB more people will run into it.

Bill

---

### Post by VMC on 2010-02-14
This Plymouth error or whoever error, is getting stranger by the minute.

Now I tried this scenario. It still freezes with Plymouth installed, but if I add nomodeset to the linux line it will boot ok, but then freeze 2 minutes every time.

Now it I then type Alt+SysRq+k (keyboard works using nomodeset & Plymouth) , then it Logs out or switches user (I'm not sure which).

After Alt+SysRq+k, I am then brought to a gui login prompt. After I then login, everything is back to normal?!

---

### Post by ranch hand on 2010-02-14
Mine, not being as badly effected as yours, has given me some hints from the on screen boot messages and behavior changes with updates.

Plymouth is obviously involved.  I think that something in the xorg stuff is involved.  I am sure that ureadahead is involved somehow.  I am also pretty sure of gdm.

I have no idea what ubiquity does in the installed OS (I thought it had to do strictly with the Live environment) but there has been an improvement with the update this morning and that was the only thing I saw that, I thought, could be responsible.

When I run "dpkg-reconfigure ureadahead plymouth gdm I usually get some improvement in any OS.

I had 3/4 boot this morning and 2/4 reboot.

---

### Post by VMC on 2010-02-14
I think your absolute right in thinking that ureadahead is envolved in this mystery. 

Thre are messages to the fact that on reboot ureadahead will change things. I did a find command on both plymouth and readahead to look at any changes after I rebooted. Plymouth works fine on the initial boot. Its the reboot that it fails.

I'm not sure who's at fault here. All I know is if I remove plymouth then I can boot fine. I wonder about stopping ureadahead from doing whatever it does...

I wish I knew how those two or tied in to this mess.

---

### Post by VMC on 2010-02-15
> **Ibidem said:**
> I don't know whether the processes would start, but you might try setting up a script to run automatically at login, with output redirected to log files:
```
cp /proc/fb ~/fb.log
#Or cat /proc/fb>~/fb.log
ps aw | grep X.*vt>~/awxvt.log
```That last command would be more troublesome:
```
sudo initctl list>~/initlist.log
```would require that you setup sudo to not ask for your password.
Then you'd be best to wait 5 minutes or so after boot and then shutdown and copy the files manually.
If you don't have any files there, it means it froze solid before running scripts.
Not quite sure which file to edit  to autorun these, but I know it can be done.

Ibidem

I saw your message on the bug report. The problem being, the system is frozen. If it wasn't frozen I wouldn't even need to redirect the output.

---

### Post by Ibidem on 2010-02-15
If you put them in a script that autoruns on boot, either it will give you the output or you can state confidently that the lockup means it never gets to that point.  These are for scripts, not for manual running.

---

### Post by VMC on 2010-02-15
> **Ibidem said:**
> If you put them in a script that autoruns on boot, either it will give you the output or you can state confidently that the lockup means it never gets to that point.  These are for scripts, not for manual running.

I don't think you fully understand the problem. 
The system freezes. No input no output.
 
Scripts running either automatically or manually have no merit.

Even if I could run an automatic script. Where do you propose it should go? One of the /etc/init files? But where?

I'm sure if it was possible, Steve Langasek would have instructed me to do so.

---

### Post by Ibidem on 2010-02-15
Do you have /etc/X11/xinit/xinitrc ?  If gdm pays any attention to that, I would put it in there.
Or you could try /etc/gdm/Session/ (I think--see [here]("http://www.ibiblio.org/oswg/oswg-nightly/oswg/en_US.ISO_8859-1/articles/gdm-reference/gdm-reference/configuration.html") for the GDM manual)
These are guesses, since I'm using a totally different setup that has no such problems (nodm, no plymouth).

---

### Post by dino99 on 2010-02-16
hm, try to remove all the plymouth related packages, but fail with libplymouth2, as it want to desinstall everything. ;)

---

### Post by sgage on 2010-02-16
You can leave libplymouth2. If you just remove plymouth, the freezing will stop. Or you can downgrade to the ~-9 version. Both have worked for me.

Now if I can only get my rig to resume from suspend properly...

---

### Post by dino99 on 2010-02-16
> **sgage said:**
> You can leave libplymouth2. If you just remove plymouth, the freezing will stop. Or you can downgrade to the ~-9 version. Both have worked for me.

Now if I can only get my rig to resume from suspend properly...

thanks, already done but it's crazy that this single lib want to remove everything, don't understand such design.

I'm sorry about resume as i don't know to help on that point; lot of discussion here about this, but still a problem for many users.

---

### Post by mc4man on 2010-02-16
For something that has no real value ... I guess I'll bit my tongue

> but it's crazy that this single lib want to remove everything, don't understand such design

Whether or not plymouth works out, or works without issue for all setups, having the shared  lib installed shouldn't be an issue. 

The reason removal would cause what you see is probably from one or 2 packages that built-depended on plymouth, most likely "mountall" is the main one.

---


---
title: "Problems with Unity"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by linux_dream on 2011-11-11
So I upgraded to the newest Ubuntu version about 1 month ago.  My Unity 3d was working too slow so I set up Unity 2d and all worked just fine.  Until I downloaded and installed all the updates possible.  When I rebooted, Unity 2d was gone.  It's been maybe a month now that I'm stuck on Windows XP.  In Ubuntu without Unity, I can't browse the internet (no firefox icon on my desktop), I can't enter a terminal, etc.  I can only go through my files.

I'd like to download the latest updates but I am not sure how to do this without Unity.  Maybe I should enter in a safe mod (it's like a terminal I think) and type some command to get the latest updates.  I'm hoping this will fix my problem.  Can someone tell me what is the command to get the latest updates?  
Thank you in advance!

---

### Post by ajgreeny on 2011-11-11
So what desktop do you get, if any?

---

### Post by linux_dream on 2011-11-11
I couldn't take a screenshot for some reason.
I have all the icons I used to have on my desktop.  I have a top bar that shows "Ubuntu Help" and where I can browse through my folders.  Also included in the bar: the same things than when you do right click over your desktop (create new folder, file, etc.).
Nothing else.

Edit:  So I can't even shut down my computer via a normal way.  I have to manually hit the reset/off button of my cpu.

---

### Post by fantab on 2011-11-11
> **linux_dream said:**
> So I upgraded to the newest Ubuntu version about 1 month ago.  My Unity 3d was working too slow so **I set up Unity 2d** and all worked just fine.  Until I downloaded and **installed all the updates possible.  When I rebooted, Unity 2d was gone**.  It's been maybe a month now that I'm stuck on Windows XP.  In Ubuntu without Unity, I can't browse the internet (no firefox icon on my desktop), I can't enter a terminal, etc.  I can only go through my files.

I'd like to download the latest updates but I am not sure how to do this without Unity.  Maybe I should enter in a safe mod (it's like a terminal I think) and type some command to get the latest updates.  I'm hoping this will fix my problem.  Can someone tell me what is the command to get the latest updates?  
Thank you in advance!

Use Ctrl+Alt+T and see if you can launch Terminal.

If you can then "Purge" Unity and Unity 2D. And reinstall Unity

---

### Post by linux_dream on 2011-11-11
> **fantab said:**
> Use Ctrl+Alt+T and see if you can launch Terminal.

If you can then "Purge" Unity and Unity 2D. And reinstall Unity
Oh nice, I could enter in the terminal.  I don't know how to purge unity and reinstall it.  If you have the commands I'd be glad to test them out right away.
By the way I typed in "firefox" and it opened just fine, I'm currently replying under Ubuntu.

Does someone know the command to runs the updates on Ubuntu?
Edit: Nevermind for the command to run the updates of Ubuntu, I've found them and I'm currently downloading+installing 178 Mb of them.  I hope this will fix Unity.  I'll let you know.

---

### Post by linux_dream on 2011-11-12
Ok I just finished the installation of the updates.  I'm still at the same point, no Unity working.  I'm waiting for the commands to purge+install Unity again.  
Thank you guys so far.

---

### Post by ajgreeny on 2011-11-12
```
sudo apt-get purge <package-names>
``` followed by ```
sudo apt-get install <package-names>
```may do the trick.  I don't use unity so could be talking rubbish, but I also wonder if you had an old compiz profile which is being loaded and may be causing big problems.

It could be worth running ```
gconftool-2 --recursive-unset /apps/compiz
```followed by ```
unity --reset
```in terminal to see if it helps.

---

### Post by linux_dream on 2011-11-12
> **ajgreeny said:**
> ```
sudo apt-get purge <package-names>
``` followed by ```
sudo apt-get install <package-names>
```may do the trick.  I don't use unity so could be talking rubbish, but I also wonder if you had an old compiz profile which is being loaded and may be causing big problems.

It could be worth running ```
gconftool-2 --recursive-unset /apps/compiz
```followed by ```
unity --reset
```in terminal to see if it helps.
Thanks a lot.  I've just tried the two last commands of your post, without success.  Here is what I get:
```
isaac@isaac-desktop:~$ gconftool-2 --recursive-unset /apps/compiz
isaac@isaac-desktop:~$ unity --reset
unity-panel-service: proceso no encontrado
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
Setting Update "command"
Setting Update "run_command_terminal_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x22001e2

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x22001f0
```I'll try the first two right now.

Edit: What do I put in "package-names"?  Unity?

---

### Post by linux_dream on 2011-11-14
Hey guys, can someone help me to find out what should I type instead of 
<package-names>?
Thanks in advance.

---

### Post by ajgreeny on 2011-11-15
> **linux_dream said:**
> Hey guys, can someone help me to find out what should I type instead of 
<package-names>?
Thanks in advance.
This may be a bit of a clunky workaround, but if you install **synaptic** package manager you can use that to search (by name alone) for all packages with **unity** in the name.  Those are possibly the packages to deal with, but be wary of, and make note of dependent packages that may be removed along with the unity packages, then make sure you reinstall those as well.

Remember that I don't use unity, so may be wrong with this information.

---

### Post by Mark Phelps on 2011-11-15
The steps in the link below will walk you through removing compiz and unity, cleaning up the remainder, and reinstalling compiz and unity:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by linux_dream on 2011-11-15
> **Mark Phelps said:**
> The steps in the link below will walk you through removing compiz and unity, cleaning up the remainder, and reinstalling compiz and unity:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
Thank you Mark.  
I'm having a hard time with following the steps.
I do follow them but then I run into troubles with the command:
```
isaac@isaac-desktop:~$ sudo service gdm restart
restart: Unknown instance:
``` so this command doesn't seem to work.
I do have Unity and the Compiz config settings manager.
When I open it, the steps says that I must verify that Unity is indeed chosen.
They say:>  At the lower left of CCSM, click 'Preferences' and make sure 'Unity' is selected under 'Profile'. 
but when I go there, I only see "By default" and "h..." where the 3 dots are unreadable characters.  I don't see anything like Unity to choose.  Thus, I can't proceed further.
What do I do now?

---

### Post by sikander3786 on 2011-11-16
> **linux_dream said:**
> Thank you Mark.  
I'm having a hard time with following the steps.
I do follow them but then I run into troubles with the command:
```
isaac@isaac-desktop:~$ sudo service gdm restart
restart: Unknown instance:
``` so this command doesn't seem to work.
I do have Unity and the Compiz config settings manager.
When I open it, the steps says that I must verify that Unity is indeed chosen.
They say:
but when I go there, I only see "By default" and "h..." where the 3 dots are unreadable characters.  I don't see anything like Unity to choose.  Thus, I can't proceed further.
What do I do now?
Sorry for being lazy about this stuff. I would update that guide in a day or so hopefully.. The guide wasn't thoroughly tested with Oneiric as it was primarily intended for Natty.

If you are using Oneiric, your command would be:

```
sudo service lightdm restart
```

As they replaced GDM with LightDM in Oneiric.

And for the 'Preferences' thing, just need to make sure that CCSM behaviour is the same in Oneiric also.

Regardless of when I get some time to update that guide, we can continue helping you in this thread so please keep us updated.

---

### Post by linux_dream on 2011-11-18
Okay thank you sikander.
So I tried "sudo service lightdm restart"  but it didn't do anything good.  It was as if I had rebooted my cpu (closed my applications and some message about my monitor poped up, as when I reboot Ubuntu).  Still no change in my missing bar(s).
In ccsm, I do not have the "Unity" choice in preferences.  There's the "default" and now I see for the other option: a square followed by "3h".  I tried it and it didn't change anything (though my cpu froze for like 2 minutes).
I'm really lost now.

---

### Post by MG&amp;TL on 2011-11-18
I personally would:

```
sudo apt-get install lubuntu-desktop
```

so that you can have a desktop, for now, then you can fix unity.

I chose lubuntu-desktop because it's light, but you can replace that with xubuntu or kubuntu-desktop if you prefer.

---

### Post by linux_dream on 2011-11-20
> **MG&TL said:**
> I personally would:

```
sudo apt-get install lubuntu-desktop
```so that you can have a desktop, for now, then you can fix unity.

I chose lubuntu-desktop because it's light, but you can replace that with xubuntu or kubuntu-desktop if you prefer.
Thank you.
Since I'm desperate, I'm trying this.  
I've downloaded it from the terminal and now it shows a message with an "<Accept>" message at the end.  But I don't know how to accept.  I've tried enter, double click, maximizing the window and double click and enter.  Nothing work.  
Here's the message (in Spanish):
```
Configuración de lxdm &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Un gestor de sesiones es un programa que le ofrece la posibilidad de         
 &#9474; entrar gráficamente a su sistema mediante el sistema X Window.               
 &#9474;                                                                              
 &#9474; Sólo puede utilizarse un gestor de sesiones para gestionar un servidor       
 &#9474; de X concreto, pero existen varios paquetes de gestores de sesiones          
 &#9474; instalados. Por favor, seleccione que gestor de sesiones debería             
 &#9474; ejecutarse de manera predeterminada.                                         
 &#9474;                                                                              
 &#9474; Varios gestores de sesiones se pueden ejecutar simultáneamente si están      
 &#9474; configurados para manejar diferentes servidores. Para conseguir esto,        
 &#9474; configure los gestores de sesiones apropiadamente, edite cada script de      
 &#9474; init en «/etc/init.d» relacionado con ellos y desactive la comprobación      
 &#9474;                                                                              
 &#9474;                                  <Aceptar>     
```

What do I do?

---

### Post by linux_dream on 2011-11-20
Bad news.  I've removed the xconf file and rebooted.  Now the borders of the windows are gone.  When I type ctrl+alt+t a totally invisible terminal pops up.  When I type "firefox" and then enter, firefox opens (that's how I know there's an invisible terminal).
I don't know how to activate lubuntu desktop.

Edit:  Looks like I've broken everything.  Is there a way that could reset Ubuntu as when I upgrated to 11.10 for the first time?

Edit 2:  I'm now thinking about formatting my Ubuntu partition (I dual boot with windows XP).  Is there a quick way to erase my current ubuntu and reinstall it easily (without any CD/ pendrive, my CD player is broken and I don't have pendrives)?

---

### Post by fantab on 2011-11-21
> **linux_dream said:**
> Bad news.  I've removed the xconf file and rebooted.  Now the borders of the windows are gone.  When I type ctrl+alt+t a totally invisible terminal pops up.  When I type "firefox" and then enter, firefox opens (that's how I know there's an invisible terminal).
I don't know how to activate lubuntu desktop.

Edit:  Looks like I've broken everything.  Is there a way that could reset Ubuntu as when I upgrated to 11.10 for the first time?

**Edit 2:  I'm now thinking about formatting my Ubuntu partition (I dual boot with windows XP).  Is there a quick way to erase my current ubuntu and reinstall it easily (without any CD/ pendrive, my CD player is broken and I don't have pendrives)?** 
During installation choose "Something Else" option and then just format the partitions that you have assigned to Ubuntu. Be careful NOT to lose any important data you may have on /home or wherever.

Most of the time it is better to reinstall than battling with the unproductive fixes. If you can, then have a separate Linux DATA partition for your personal Data, which you mount or automount later, instead of using /home. just use "/" as mount-point. This will make is easier for you during upgrades or reinstalls to format / partition without worrying about losing data. Just a Thought.

Good Luck

---

### Post by linux_dream on 2011-11-23
> **fantab said:**
> During installation choose "Something Else" option and then just format the partitions that you have assigned to Ubuntu. Be careful NOT to lose any important data you may have on /home or wherever.

Most of the time it is better to reinstall than battling with the unproductive fixes. If you can, then have a separate Linux DATA partition for your personal Data, which you mount or automount later, instead of using /home. just use "/" as mount-point. This will make is easier for you during upgrades or reinstalls to format / partition without worrying about losing data. Just a Thought.

Good Luck
Thank you for the luck.  I called a friend and asked if he could format+install a stable version of Ubuntu with his pendrive.  That's what he's done.
So now I'm back with Ubuntu 10.04, everything working just fine.
He explained me the same thing as you: that I could create a partition with /home to save all the important data on it.  Instead, I'll just stick with what I've done so far.  I use windows XP partition for important files (I've never broken anything under windows xp since 2007; unlike Ubuntu).
So now I don't have problems with Unity, in fact I don't even have it.

---


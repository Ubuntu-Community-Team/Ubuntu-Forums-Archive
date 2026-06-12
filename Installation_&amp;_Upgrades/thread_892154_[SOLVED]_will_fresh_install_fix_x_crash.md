---
title: "[SOLVED] will fresh install fix x crash"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by jesse c on 2008-08-16
Somehow i crashed my nvidia x server access and cant figure how to restart x by terminal commands.Im wondering if i can just reload a fresh install of Hardy but i dont know how to remove the present one or is the x server not part of the os package? By the way this is a dual boot install done by live cd install disc,and the x crash might have affected my Vista system cause when i try to see my posts on ubuntu forums i get a long page of computer program text so im using a borrowed laptop for this post.thanks JESSE C

---

### Post by pytheas22 on 2008-08-16
Ubuntu shouldn't be able to do anything that can affect Windows.

Reinstalling Ubuntu would solve the issue with X--X is part of the Ubuntu package and will be removed and reinstalled along with the rest of the operating system--but there should be an easier way to get X working again.

First of all, press control-alt-F7 and you should be brought to a command-line where you can log in.  If you type:
```

startx
```

X may start again; if not, it should tell you why it couldn't start.  If you get an error message, please post it here (or at least the gist of it).

You can also try this command:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

which will automatically reconfigure the X server; there's a good chance that that will solve the problem.

---

### Post by jesse c on 2008-08-17
PYTHEAS22 thanks for reply.I just tried your cntrl/alt/f7 and just got a blank screen with blinking bar in upper left corner.i typed in code anyway and nothing,and i had to power-off to escape.I restarted and went to terminal (in low graphics mode,which its stuck in) and typed sudo startx.This is what comes up

X:warning;process set to priority -1 instead of requested priority 0
fatal server error:
server is already active for display 0
  if this server is no longer running,remove /tmp/.x0-lock and start again

i suppose this is giving me a solution but i dont know how to implement it.Can you tutor?thanks JESSE C

---

### Post by pytheas22 on 2008-08-17
Try pressing control-alt-F7 again, and then control-alt-backspace.  This should kill the X server that you have running, and force it to restart.  If it doesn't restart and you get dumped to a terminal, try typing "startx."  If it just hangs at a black screen, press control-alt-F2, which should bring you to a prompt where you can log in.  At the prompt, run:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

and then reboot (you can reboot by typing "sudo init 0") and see if the problem is resolved.

Also, I'm a bit confused because you say that X is running in "low graphics" mode.  Do you mean that you are seeing a graphical desktop, just at a low resolution?  Or are you seeing nothing besides white MS-DOS-style text on a black screen?

---

### Post by jesse c on 2008-08-17
thanks for sticking with me PYTHEAS22.The cntrl/alt/f7 worked but the cntrl/alt/f7 gave me a [H] so i cntrl/alt/f2 and did the sudo prompts but no change after restart(it didnt reboot by the other sudo prompt it just shut down so i repowered).And yes i do have a graphics screen but it is very large.Also when i go onto 'Appearance Preference'/Visual Effect system page where i have three choices   NONE-NORMAL-EXTRA it wont accept NORMAL or EXTRA because it says my graphics settings are too low to enable.This card NVIDIA 6150le worked fine for the last couple of years.Am i trying to fix the wrong problem?When i go to 'system/xserver config it still says its not enabled,and my 'screen resolution 'setting wont go higher than something like 800/600 when i used to have it set 1200/1000 with many options above and below that

---

### Post by jualin on 2008-08-17
> **jesse c said:**
> thanks for sticking with me PYTHEAS22.The cntrl/alt/f7 worked but the cntrl/alt/f7 gave me a [H] so i cntrl/alt/f2 and did the sudo prompts but no change after restart(it didnt reboot by the other sudo prompt it just shut down so i repowered).And yes i do have a graphics screen but it is very large.Also when i go onto 'Appearance Preference'/Visual Effect system page where i have three choices   NONE-NORMAL-EXTRA it wont accept NORMAL or EXTRA because it says my graphics settings are too low to enable.This card NVIDIA 6150le worked fine for the last couple of years.Am i trying to fix the wrong problem?When i go to 'system/xserver config it still says its not enabled,and my 'screen resolution 'setting wont go higher than something like 800/600 when i used to have it set 1200/1000 with many options above and below that

You are getting this issues because the xorg reconfiguration command you use probably restore the Generic Drivers (not the 3D ones). Now you only need to install the propietary Nvidia Drivers. Try going to System, Administration, Hardware Drivers (on 8.04) and enabling the nvidia drivers. If not you can use Envyng-gtk found on Synaptic Package Manager to install the correct drivers for you. Good luck, and feel free to ask us!

---

### Post by pytheas22 on 2008-08-17
Yes, as the poster above says, the problem could lie with the nvidia driver.  Try opening your xorg.conf file:

```
sudo gedit /etc/X11/xorg.conf
```

and about halfway down you should see the "Device" section, which probably looks similar to:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Try adding in a line to specify which driver to use, e.g.:
```

Section "Device"
	Identifier	"Configured Video Device"
        driver          "nvidia"
EndSection
```

Then save the file and press control-alt-backspace to restart X.  If the problem still persists, try changing the driver to "nv" by replacing "nvidia" with "nv" in the "driver" line.

In case this breaks X and stops your desktop from loading at all, keep in mind that you can edit xorg.conf from the command-line by pressing control-alt-F2, logging in and typing:

```
sudo nano /etc/X11/xorg.conf
```

That way you can always change it back to what it was to begin with if necessary.

---

### Post by jesse c on 2008-08-17
thanks JUALIN i tried your approach way back with no luck.PYTHEAS22 i tried your commands both the 'nvidia' and the 'nv',no luck but there was no driver spot where you said to look so i added it like you suggested.I have posted in "instillations" forum to learn how to reinstall a fresh start from live cd but im willing to try some more fixes since i might make a mess of that too.Thanks for all your ideas i enjoy the learning experience but you must be getting as frustrated as i am by this point

---

### Post by pytheas22 on 2008-08-17
Yes, a clean install will definitely solve the problem, and I'm sorry none of the above helped.  There are still other things that you could try, but they'd probably take more time than it would to just reinstall.

Reinstalling is easy--just boot to the live CD, start the installer and in the partitioning section, choose to install Ubuntu in the same partition in which your old system exists (and make sure to format the partition).  That way it will just overwrite the existing system.  If you need more help with that and no one responds in your other thread, you can ask here.

---

### Post by jualin on 2008-08-18
I agree with pytheas22 just go for the reinstall, it should save you some time. ;)

---

### Post by jesse c on 2008-08-18
PYTHEAS22 easy for you ,scary for me.See my other post in 'installations' section.Im having questions on finding the right partition to overwrite and how to do that,and now i have to format that partition.Wasnt that done the first install?,and isnt that done automatically?Its been years since my first install but i dont remember being smarter back then,but memory isnt one of my strong points  JESSE C

---

### Post by jesse c on 2008-08-19
SOLVED:i dont even know how i did it but ill aim credit to a post i found deep in a"nvidea x driver"google.On a page headed 'linux-meta in ubuntu question #35909' in a post by Enrico Rosina he starts a solution to a similar problem to mine with a 'apt-get remove --purge nvidia*' command that ended with a positve solution even though his steps two and three were duds,but now i was working from a blank slate and went into synaptic and tried a nvidia package,(actually several tries) and then went into system/restricted driver which poped up a window saying i needed a linux generic restricted driver package,so i paged thru synaptic till i found something that sounded close and applied it and success!Now i have to learn how to remove a bunch of failed boot file changes that i made in my experiments looking for solutions but that will be a new post. thanks PYTHEAS22 ,JUALIN and SEF for sticking with me.This all came about from my paranoia with reinstall partitioning   JESSE C

---

### Post by jualin on 2008-08-19
Glad the problem is now solved.

---

### Post by jesse c on 2008-08-19
PYTHEAS and JUALIN thanks for your efforts,i took your hints and went for the fix instead of the reinstall-what did i have to lose at that point.I purged all nvidia and reinstalled from scratch and it worked-somehow.I give props in my other thread 'cause i wouldnt have thought of it or known the command line but a little research and forum help from you guys gave me a smidge mo smarts.Keep on helpin  JESSE C

---


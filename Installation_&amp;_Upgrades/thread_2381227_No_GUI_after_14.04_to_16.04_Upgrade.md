---
title: "No GUI after 14.04 to 16.04 Upgrade"
date: 2017-12-28
forum: Installation &amp; Upgrades
---

### Post by donestephens2 on 2017-12-28
Hi Guys

Long running 14.04 installation with no problems on a Gigabyte motherboard with AMD cpu and integrated ATI 6400 HD graphics.  I did not have to do anything special that I recall when I built the server nearly 4 years ago. 

Prompted for the version upgrade, I accepted it and the upgrade ran. After reboot, grub looks normal. Then I see the purplish screen with the Ubuntu logo and the five dots progress graphic. When it finishes, instead of a GUI login, I get a console screen on my monitor that looks like this. 

     Ubuntu 16.04.3 LTS hostname tty1
     hostname login: 

I can login and the account seems to work fine. However, no GUI ever happens. 

     startx -- fails, unless I use sudo.
     sudo startx -- switches to GUI mode. The screen turns the color of the desktop background, but there are no interactive elements. Mouse moves, but nothing todo. Right-Click doesn't show any menu (I don't remember if it should, just saying). No dock or Unity or menus or anything.  Nothing changes if you move the mouse around to the different edges or corners. 

I can ctrl-alt-F1 to get back to a terminal window, or ctrl-alt-F3 to return to the non-interactive GUI window, but nothing else. 

I have searched these forums and found people with similar problems, which lead to the following attempted fixes. 

sudo dpkg --configure -a
sudo apt-get update 
sudo apt-get install --install ubuntu-desktop
sudo apt-get -f install 
sudo apt-get install unity

lightdm and sudo lightdm don't work
unity -- complains about no DISPLAY value set. Set the value and ran again, but no difference.

Some user suggested

      dconf reset -F /org/compiz -- fails. Usage message says should be "-f" instead. Still fails. /org/compiz is not a valid path. (Don't know if it should be.)

Someone suggested 

     sudo rm -fr ~/.cache/compizconfig-1---but this doesn't exist. 
     sudo rm -f ~/.compiz/--also didn't exist.
     sudo apt-get install --reinstall ubuntu-desktop unity compizconfig-settings-manager
 
Someone suggested 

     mv ~/.config ~/.notconfig. 

All of these groups of commands were implemented, and then success was tested before and after a reboot, but nothing changed. 

Any insight anyone has to offer will be appreciated. 

Don

---

### Post by deadflowr on 2017-12-28
Did you have the amd closed source drivers installed for 14.04?

---

### Post by donestephens2 on 2017-12-28
I don't remember having to install any additional AMD drivers, and I am not doing anything with the server that makes GUI performance matter. So I could be wrong as to memory, but if the GUI worked without the drivers, then I would have had no reason to install them. 

Thanks. 

Don

---

### Post by donestephens2 on 2017-12-31
I am still stuck on this.  Any suggestions anyone has will be appreciated. 

Don

---

### Post by Bashing-om on 2017-12-31
donestephens2; Hello .

let's start here:
> 
sudo startx -- switches to GUI mode. 

results in "root" owning "your" desktop - NOT "you" .
Proof:
```

ls -al .ICEauthority .Xauthority

```
Should be similar:
> 
sysop@x1604:~$ ls -al .ICEauthority .Xauthority
-rw------- 1 sysop sysop 6280 Dec 31 11:26 .ICEauthority
-rw------- 1 sysop sysop   50 Dec 31 11:26 .Xauthority
sysop@x1604:~$

where my username is sysop.

Then next is the graphic's driver situation.
show: output between code tags
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

sudo lshw -C display
dpkg -l fglrx*
fglrxinfo
lsmod | grep radeon

```
to see what is .. and a hint where to go to next .

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by lithehelium on 2018-01-01
Can you install KDE plasma
code 
```
sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get install kubuntu-desktop

```
```
startx 
```
lf it did`n work to sudo -i
then startx

---

### Post by donestephens2 on 2018-01-02
Hi Bashing-om

I see indeed that after running "sudo starts", the ownership of .Xauthority was changed to root from my user id.  I don't know whether or not is was necessary for me to change ownership back to my user id, but I did anyway. 

So now, for the outputs you requested:

sudo lshw -C display

```

  *-display            
       description: VGA compatible controller
       product: Richland [Radeon HD 8470D]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:52 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff

```

dpkg -l fglrx*

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name               Version        Architecture   Description
+++-==================-==============-==============-=========================================
un  fglrx-glx          <none>         <none>         (no description available)

```

fglrxinfo

```

fglrxinfo: command not found

```

I double-checked to make sure that fglrxinfo was not on my system.

lsmod | grep radeon

```

radeon               1522942  1
i2c_algo_bit           13413  1 radeon
ttm                    93424  1 radeon
drm_kms_helper         55071  1 radeon
drm                   303102  3 ttm,drm_kms_helper,radeon

```

Thanks. 

Don

---

### Post by Bashing-om on 2018-01-02
donestephens2; hummm ...

yeah ya done good to chmod the files back to you .. Might check in /home that all files belong to "you" with the exception of the '..' directory. 

There "should" have been no output at all from dpkg -l fglrx* .
Maybe some vestiges of the old fglrx driver remains ?
what results:
```

sudo apt remove --purge fglrx*

```

Appears that the radeon driver is loaded .

And what is the desktop environment(s) ?
show us:
```

ls /usr/share/xsessions

```

We consider what it will take to start the GUI from terminal. See here what we can find out.

[INDENT][INDENT]let there be GUI
[/INDENT][/INDENT]

---

### Post by donestephens2 on 2018-01-03
Hi Bashing-om

So my ability to ssh into the box died. I connected a monitor and restarted it. When it came up, there was a message prompting me that 900+ packages needed to be updated. I ran the "sudo apt-get upgrade" and ran updates for a long time. After that, I rebooted it, and my GUI is magically restored. 

Thanks for your time and your patient suggestions.  

Good to go now. 

Don

---

### Post by Bashing-om on 2018-01-03
donestephens2; Wow ...

Who wudda thunk it ?

Real glad things worked out !

As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]we can see clearly now
[/INDENT][/INDENT]

---


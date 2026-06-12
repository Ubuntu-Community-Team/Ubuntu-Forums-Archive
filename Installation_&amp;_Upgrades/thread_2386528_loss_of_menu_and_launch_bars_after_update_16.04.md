---
title: "loss of menu and launch bars after update 16.04"
date: 2018-03-07
forum: Installation &amp; Upgrades
---

### Post by erica-rowancott on 2018-03-07
Yesterday morning I accepted the weekly update to Ubuntu 16.04 on my laptop and since then have lost both menu and launch bars. I can get a command line by right clicking on background but it does not have a menu bar either and cannot be resized or moved nor can any other application I launch via command line. Also alt-tab does not work to move between applications. If I login as "guest" after rebooting the screen appears exactly as it should with launch bars and status bars etc - how can I get this functionality back to my proper login account?

---

### Post by kerry_s on 2018-03-07
where you using extensions?

in that terminal:
mv -rf ~/.local/share/gnome-shell ~/.local/share/gnome-shell.bak

then reboot or log out/in

---

### Post by erica-rowancott on 2018-03-07
I don't even know what extensions are so probably not using them. On another forum I saw advice for a similar problem to install Ubuntu tweak and have done that but it doesn't help either. I'll try you suggestion but given that without alt-tab I cannot switch between applications it takes an age to get back to this point (no menu bars also means no means of accessing history or bookmarks!)

---

### Post by erica-rowancott on 2018-03-07
Ok I tried mv -rf ~/.local/share/gnome-shell ~/.local/share/gnome-shell.bak and got message the -r was not a valid option

---

### Post by kerry_s on 2018-03-07
wait, it won't work. i had a brain fart.
i keep forgetting 16.04 is running unity.
i think the 1 you want is unity tweak.
can you still use the windows key to access dash?

---

### Post by erica-rowancott on 2018-03-07
my keyboard doesn't have a windows key sadly. can I  *access dash from a command line as that is about all I can do presently?*

---

### Post by kerry_s on 2018-03-07
then how about alt+f2 
theres a command to reset unity, i just can't remember.
I'm currently in the middle of a install, so i only have my phone.

---

### Post by erica-rowancott on 2018-03-07
alt-f2 does nothing. If I type dash in command line it gives me a prompt but I don't know what to type, is there anywhere I should be looking for command to reset unity? Thanks for trying to help though in mid-install!

---

### Post by kerry_s on 2018-03-07
in terminal
unity --reset

---

### Post by erica-rowancott on 2018-03-07
Ok this is what happened:
erica@erica-W54-55SU1:~$ dash
$ unity --reset
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
We're already using profile 'unity', no need to switch
The --reset option is deprecated, You should run with no options instead.
unity-panel-service stop/waiting
unity7 stop/waiting
unity-panel-service start/running, process 2950
unity7 start/running, process 2981

No change to screen but I'll try rebooting now

---

### Post by erica-rowancott on 2018-03-07
after reboot, nothing new. When login screen comes up it looks fine with status bar across the top showing time, network status etc but as soon as I actually login screen goes blank apart from background plus the single shortcut I had stored on it - no menu bars or launch bars still.

---

### Post by erica-rowancott on 2018-03-07
reboot didn't help nor did searching for and installing latest update. seems only option is to set up another user account but that is going to be a nightmare to get access to all my stuff.

---

### Post by kerry_s on 2018-03-07
did you try running "unity" from the terminal?

---

### Post by erica-rowancott on 2018-03-07
yes and made no change to appearance - this is the result in the command line:
erica@erica-W54-55SU1:~$ unity
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
We're already using profile 'unity', no need to switch
unity-panel-service stop/waiting
unity7 stop/waiting
unity-panel-service start/running, process 2873
unity7 start/running, process 2943
erica@erica-W54-55SU1:~$

---

### Post by erica-rowancott on 2018-03-07
There are lots of folk with same problem - some on Ask ubuntu, and also on Canonical's launcher.net - none have come up with a proper solution yet for cross reference here are the links:
[https://answers.launchpad.net/ubuntu/+question/665349](https://answers.launchpad.net/ubuntu/+question/665349)
[https://askubuntu.com/questions/1011582/launcher-and-menu-bar-no-longer-visible-after-mar-2-2018-update](https://askubuntu.com/questions/1011582/launcher-and-menu-bar-no-longer-visible-after-mar-2-2018-update)

---

### Post by Frogs Hair on 2018-03-07
Unity/Compiz Reset commands:

```
sudo apt-get install dconf-tools
``````
 dconf reset -f /org/compiz/
``` Unity Reset: ```
setsid unity
```

Icons to default with Unity running: 
```
unity --reset-icons
```

---

### Post by kerry_s on 2018-03-07
i'm thinking it's got to be some kind of messed up permissions thing.
unity is working, it is running, just not displaying.

what are your thoughts on just removing the entire .config & .local folder from command it should be recreated on log in yes?

---

### Post by Frogs Hair on 2018-03-07
> **kerry_s said:**
> i'm thinking it's got to be some kind of messed up permissions thing.
unity is working, it is running, just not displaying.

what are your thoughts on just removing the entire .config & .local folder from command it should be recreated on log in yes?

If your asking me , I've not tried that . I know some users have renamed .config as old in gnome creating a new healthy one post login. In Unity, I just don't know. Creating a new user maybe a worth a try also to see if the account runs properly.

---

### Post by kerry_s on 2018-03-07
i just downloaded ubuntu 16 & i'm getting it loaded in vm.

i was going to grad a snapshot after updating & then see what would happen.

---

### Post by kerry_s on 2018-03-07
alright it looks like it would be fine, .config was recreated right after removal & .local was recreated after reboot, everything was set back to stock.

so the commands for terminal:
rm -rf ~/.config
rm -rf ~/.local
sudo reboot

---

### Post by erica-rowancott on 2018-03-08
I also tried these commands and got:
erica@erica-W54-55SU1:~$ setsid unity
erica@erica-W54-55SU1:~$ compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
We're already using profile 'unity', no need to switch
unity-panel-service stop/waiting
unity7 stop/waiting
unity-panel-service start/running, process 3915
unity7 start/running, process 4043
^C
erica@erica-W54-55SU1:~$ unity --reset-icons
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
We're already using profile 'unity', no need to switch
unity-panel-service stop/waiting
unity7 stop/waiting
unity-panel-service start/running, process 4102
unity7 start/running, process 4184
erica@erica-W54-55SU1:~$ 

Each time unity was entered on the command line there was a quick flash up of some kind of window but it disappeared too fast to see what.

---

### Post by erica-rowancott on 2018-03-10
OK Guys, I have found the solution posted in another forum and it works for me and at least two others - very simple. Open a terminal by right clicking on the background then type in this command:
sudo -r ~/.cache
then reboot.

---

### Post by roseruby on 2018-03-11
Thank you so much! Been having the same problem for days now and clearing out the cache did the trick. :KS

---

### Post by buckcw on 2018-03-13
> **erica-rowancott said:**
> Open a terminal by right clicking on the background then type in this command:
sudo -r ~/.cache
then reboot.

Thanks for sharing. It worked for me, or to be precise the rm command worked ;)

[INDENT][FONT=courier new]sudo rm -r ~/.cache[/FONT][/INDENT]

Thanks again!

---

### Post by jack.edgewood on 2018-03-15
Hello everyone!

Im using Ubuntu 16.04.04 LTS. I did an updated yesterday evening and this morning by starting my computer menu and dash are missing. 

1.) I tried to clear the cache as suggested (terminal -> sudo rm -r ~/.cache), but i did not work for me. 

2.) I tried to login as a guest, but the screen is still blank and i had to open console one by ctl+alt+F1 and sudo reboot. 

3.) Opening a terminal by right click and then unity --reset or unity --reset-icons did not work either.
As of 3.) i get error messages in terminal, as is:

compizconfig - Error: Unable to find interface type 3 on 0x10065b0
[... ]
unity-panel-service stop/waiting
 unity-panel-service start/running process 2798 
start: Job failed to start

I am out of ideas now, as im not an expert for unity or desktop GUIs in general. 

What happend and how do i get my menus and dash bar back? Thanks for reading this and your support! :) Jack.

##
There are more people having this problem after the update/upgrade.
[https://askubuntu.com/questions/1015065/dash-top-panel-and-title-bars-of-windows-are-not-being-displayed/1015159#1015159](https://askubuntu.com/questions/1015065/dash-top-panel-and-title-bars-of-windows-are-not-being-displayed/1015159#1015159)

---

### Post by jack.edgewood on 2018-03-15
Okay, i got it working again. This did the trick for me:

> 
rm -rf ~/.compiz-1 ~/.config/compiz-1
sudo shutdown now

reboot PC


This will delete all of your customization of Dash... :( 

But at least Dash and Menu are back! Btw. this bug is unfixed for 7 years, 3 month now.
[URL="https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444"]
[https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

[https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444](https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/1285444)

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1212987](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1212987)



[/URL]

---


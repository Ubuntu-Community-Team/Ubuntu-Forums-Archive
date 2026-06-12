---
title: "I just installed v9.10 and I'm really struggling with the new features."
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by Akira_Oni on 2010-03-31
I'm a student at a college which requires windows for much of it's instruction, so for the last year I've been using windows almost constantly. It wasn't "bad", as I was using a windows 7 beta, but it still isn't Ubuntu.

Last night I installed for the first time in about a year. After installing from the core Ubuntu 9.10, I then "upgraded" to Ubuntu Studio. I haven't found all of my issues, but I have alot of them now and I wonder if you can help me.

First: I have a Wacom Intuos4, and while ubuntu found my Wacom it hasn't done much else with it. Pressure sensitivity doesn't work, nor do I know how to change it. I found this: [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

Ubuntu returns this error:

```

akiraoni@Lazarus:~$ sudo $xsetwacom set Stylus PressCurve 0 15 85 100
[sudo] password for akiraoni: 
sudo: set: command not found

```

All of the commands for xsetwacom are followed by "set." What do I do?

My second issue is with the sounds. In the older flavors of ubuntu I had access to my sound themes. If I didn't like something, I could change it. Now the only thing I can control is the theme itself. This distro opens with some ambient sounds. I miss my drumbeats. :( How do I change the sounds in a theme?

My third issue is actually with my menu bar. I prefer my menu on the right side with my access bar on the top of my screen. However when I set this up like that, there was a conflict with a gradient that the menu bar keeps insisting on using. It honestly looks ugly as sin, and the only way I've been able to resolve it is if I make the entire bar black. That works for now, as I have a black background (this frog is cute), but it's not a permanent solution. I need to find a way to change that gradient or make the bar a single flat color.

I actually have more issues, but those seem to be with Ubuntu Studio and I'll go make a more specific post about them when I find all my bugs. Any help will be appreciated. ^_^

---

### Post by 98cwitr on 2010-03-31
my first guess is that wacom is not properly configured or installed correctly. 

if you just do 

```
sudo $xsetwacom --help
``` what does it return?

---

### Post by Akira_Oni on 2010-03-31
```
akiraoni@Lazarus:~$ sudo $xsetwacom --help
sudo: invalid option -- '-'
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

```

---

### Post by 98cwitr on 2010-03-31
take off the $ in front of the xsetwacom and see what happens. The website's info page does specifically have the $ as part of the command. It's looking like it's not recognizing $xsetwacom as a command, but to be sure you could also take the sudo off and test that as well.

---

### Post by Akira_Oni on 2010-03-31
```
akiraoni@Lazarus:~$ sudo xsetwacom --help
[sudo] password for akiraoni: 
Usage: xsetwacom [options] [command [arguments...]]
Options:
 -h, --help                 - usage
 -v, --verbose              - verbose output
 -V, --version              - version info
 -d, --display disp_name    - override default display
 -s, --shell                - generate shell commands for 'get'
 -x, --xconf                - generate X.conf lines for 'get'

Commands:
 list [dev|param]           - display known devices, parameters 
 list mod                   - display supported modifier and specific keys for keystokes
 set dev_name param [values...] - set device parameter by name
 get dev_name param [param...] - get current device parameter(s) value by name
 getdefault dev_name param [param...] - get device parameter(s) default value by name

```

---

### Post by 98cwitr on 2010-03-31
and that's it...take off the $ for future usage of this program

---

### Post by Akira_Oni on 2010-03-31
I'm gonna have to create a new post for my other issues huh?

---

### Post by Akira_Oni on 2010-04-01
I think my xsetwacom is broken.

```
akiraoni@Lazarus:~$ sudo xsetwacom -s get Stylus PressCurve
[sudo] password for akiraoni: 
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'Stylus'

```

I thought this meant that it just wasn't installed, so I tried doing an install of it. 

```
akiraoni@Lazarus:~$ sudo apt-get install xserver-xorg-input-wacom wacom-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-wacom is already the newest version.
wacom-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 141 not upgraded.
```

What am I doin wrong?

---


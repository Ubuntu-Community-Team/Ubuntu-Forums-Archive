---
title: "[SOLVED] Octave 2.9 Broken"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by run4flat on 2008-02-26
Greetings all -

When I upgraded to 7.10 months ago, the upgrade broke my octave2.9 branch.  This wasn't a major problem because 2.1 worked for most of my uses.  However, I believe my work now puts me closer to the edge of octave's capabilities, which means 2.1 isn't working so hot for me.

Here's what went wrong: After the upgrade, octave 2.9 no longer knows where to find the function dlmread.  It also cannot locate pcolor.  However, it can locate such functions as wavwrite and plot.  I'm fairly certain that the files are on the machine and it may simply be a matter of correcting a corrupt file telling octave where to find these function files.  However, I don't know how to locate such a configuration file, assuming that's the problem.

I have repeatedly (completely) uninstalled both branches of octave in hopes that the problem would correct itself but I've had no luck and nobody else seems to have had this problem.

Can anybody point me in the right direction?

David

---

### Post by Partyboi2 on 2008-02-26
when you uninstalled octave 2.9 did you remove the config files as well before reinstalling the package?
```
sudo apt-get remove --purge --reinstall octave2.9
```


---

### Post by run4flat on 2008-02-28
Thanks for your response.

_Results_: Unfortunately, that did not do it.  Actually, the command-line you suggest didn't reinstall octave 2.9, either, it just removed it.  I then reinstalled the software with the appropriate apt-get.  I fired up octave 2.9 and typed
```
help dlmread
```
and got the standard response for unknown functions:
```
help: `dlmread' not found
```

_Remarks_: I don't use the command-line very often to install software because I almost always use Synaptic.  You suggest using the --purge option; it's not clear from the documentation, but isn't that just like using Synaptic's "Mark for Complete Removal" option?  I have done that before, with the same results.

Again, I wouldn't mind digging deeper but I don't know where to look.  Any other ideas?

---

### Post by Partyboi2 on 2008-02-28
Yes purge  is the same as using Synaptic's "Mark for Complete Removal" option. Have you thought of skipping 2.9 and installing 3.0 from source? [Here]("http://ubuntuforums.org/showthread.php?t=680690") is how to and can get 3.0 from [here]("http://www.gnu.org/software/octave/download.html") if interested. Maybe 3.0 will work better for you, otherwise I have know other ideas :)

---

### Post by run4flat on 2008-03-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/octave2.9-forge/+bug/157050](https://bugs.launchpad.net/ubuntu/+source/octave2.9-forge/+bug/157050) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Partyboi -

Thanks for all your help.  I tried your suggestion and attempted to compile octave 3.0 from source but ran into some other troubles.

I didn't want to spend more time figuring that out - I would rather have something working that gets updated from the repositories for me so I don't have to maintain it myself.  After a bit of digging I learned about the file ``~/.octaverc'', which holds all of the octave stuff just like any other ``~/.<prog-name>rc''.  I've never really messed with these files much.

The original problem that I had was posted on launchpad at [https://bugs.launchpad.net/ubuntu/+source/octave2.9-forge/+bug/157050](https://bugs.launchpad.net/ubuntu/+source/octave2.9-forge/+bug/157050).  My ``solution'' is to add the following line to my ``~\.octaverc'' file:
```
addpath(genpath('/usr/share/octave/site/api-v22/m/octave2.9-forge'), "-end");
```

The second argument (the "-end") is necessary to be sure the various paths are added to the end of the current path, which is necessary to keep the plotting functions operational. Otherwise, I had trouble with the `drawnow' function (and therefore could not use the plot command!).

While this solution works, it's not a terribly nice solution because I get over 100 copies of the message
```
warning: autoload: `' is not an absolute file name
```
I don't know what is causing these or how to fix them.

However, everything seems to be working!  Except one thing, which is that the mouse won't zoom anymore.  ?

---


---
title: "E: dkpg was interrupted error when updating"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by spiralx on 2009-12-13
Just tried to update and got this:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

..........................................................................................

If I open a terminal and type that in, I get a list of options.  Can anyone explain?

---

### Post by hansdown on 2009-12-13
Hi spiralx.

If you copy and paste into a terminal, it should ask for your password.

The spacing is important.

```
sudo dpkg --configure -a
```

---

### Post by howefield on 2009-12-13
> **spiralx said:**
> If I open a terminal and type that in, I get a list of options.  Can anyone explain?

If it isn't working as expected, post the options you are referring to, screenshot maybe ?

---

### Post by pifactory on 2009-12-13
I've had the same problem. This is what I get:

sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
aiysha@aiysha-laptop:~$ sudo --configure -a
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

What to do next?

Thanks

---

### Post by NoaHall on 2009-12-13
> **pifactory said:**
> I've had the same problem. This is what I get:

sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
aiysha@aiysha-laptop:~$ sudo --configure -a
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

What to do next?

Thanks

What on earth are you entering into the terminal?
Can you please post a screenshot of what you're entering.

---

### Post by pifactory on 2009-12-13
In terminal I enter:

sudo dpkg --configure -a

The following is returned:


sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
{-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

---

### Post by howefield on 2009-12-13
> **pifactory said:**
> 
aiysha@aiysha-laptop:~$ sudo --configure -a
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

You haven't entered the command correctly.

---

### Post by spiralx on 2009-12-17
Thanks for that.  I had also missed the gap before "-a" at the end!

duh!

But now - running it correctly, I get this:

dpkg:  dependency problems prevent configuration of dnsutils:
dnsutils depends on libbind9-50 (=1:9.6.1.dfsg.P1-3ubuntu0.2); however
Version of linbind9-50 on system is 1:9.6.1.dsfg.P1-3

Also a similar message for bind9-host.

But - up to about a week ago - it updated just fine.  So somewhere it's taken on an update or addition that's screwed with the system.   Now I have added Compiz Fusion, and some odds and ends from Synaptic, but haven't a clue now just what. 

Is there a relatively easy way to restore the correct dependencies?

---

### Post by spiralx on 2009-12-17
The above actually helped, in a funny kind of way!

With that info to hand, I went to Synaptic; which showed me that I had 2 "broken packages".  When I tried to un-install, it asked me to use Broken Filters to find them first.

Down in the bottom-left corner I used "Custom Filters" and chose "Broken" from its list.

That showed me both bind9host and dnsutils as the two broken pacakges - which I already knew.

Then I used "Package - Force Version" from the menu bar (again, as Synaptic suggested)  to force an un-install of the two wrong packages, and then force a fresh install of the correct item.

Now it seems to be updating OK!  It did ask me if I wanted to keep the version of grub I have (the new one, 0.97, to which I said yes).

Thanks for your help, guys!

---

### Post by nibirumarduk on 2009-12-17
> **spiralx said:**
> Thanks for that.  I had also missed the gap before "-a" at the end!

duh!

But now - running it correctly, I get this:

dpkg:  dependency problems prevent configuration of dnsutils:
dnsutils depends on libbind9-50 (=1:9.6.1.dfsg.P1-3ubuntu0.2); however
Version of linbind9-50 on system is 1:9.6.1.dsfg.P1-3

Also a similar message for bind9-host.

But - up to about a week ago - it updated just fine.  So somewhere it's taken on an update or addition that's screwed with the system.   Now I have added Compiz Fusion, and some odds and ends from Synaptic, but haven't a clue now just what. 

Is there a relatively easy way to restore the correct dependencies?

Make it a standard policy to only upgrade and dist-upgrade with aptitude and with the following commands:

sudo aptitude update && sudo aptitude safe-upgrade or sudo aptitude full-upgrade
For a full listing of aptitude options, type aptitude -h

Using aptitude may just save you a ton of headaches even heart attacks, for unlike apt-get, it has a smart problem resolution mechanism built-in. In different situations, aptitude can present to you quite a few (sometimes all radically different from one another) possible options including the removal of certain other packages for the installation of the package concerned or a dist-upgrade to proceed smoothly ahead.

---

### Post by spiralx on 2009-12-17
Thanks for that suggestion!  I'm wary of the command-line, for the same reason I am wary of MS-DOS:  you have to get your typing exact - or else!

But if it'll help, then I'll bite the bullet!  Still puzzled, though,  as to how it ended up with 2 wrong packages....

---

### Post by nibirumarduk on 2009-12-17
> **spiralx said:**
> Thanks for that suggestion!  I'm wary of the command-line, for the same reason I am wary of MS-DOS:  you have to get your typing exact - or else!

But if it'll help, then I'll bite the bullet!  Still puzzled, though,  as to how it ended up with 2 wrong packages....

Well, it can be due to a variety of factors including that of using packages from the ppas or other 3rd-party, non-official Ubuntu sources. More often than not, such users do not traverse the directories i.e. goto the relevant dist e.g. karmic -> repo e.g. main -> arch e.g. binary-i386 to inspect the Packages file to see what are the packages provided by a certain ppa or 3rd-party source. E.g. while you may like to have a more updated version of say emesene and while a search on launchpad shows that Philip Johnson's repo (i.e. # deb [http://ppa.launchpad.net/philip5/extra/ubuntu](http://ppa.launchpad.net/philip5/extra/ubuntu) karmic main) carries it, you may not want some other packages from this repo though e.g. nvidia-195-libvdpau.

As for making mistakes on the commandline. look at it this way, it is all about getting the hang of it. There are occasions, not saying that it'll definitely occur to you but they may e.g. a package fails to installs or upgrade because a file that belongs to it is already present in another existing installed e.g. package

dpkg: error processing /var/cache/apt/archives/xbmc-bin_1%3a9.11~beta2-karmic25640_i386.deb (--unpack):
 trying to overwrite '/usr/share/xbmc/xbmc.bin', which is also in package xbmc-common 0:9.11~beta1-karmic2

In such a situation, you may have no choice but to resort to the terminal and issue the following:
sudo dpkg --force overwite -i /var/cache/apt/archives/xbmc-bin_1%3a9.11~beta2-karmic25640_i386.deb; sudo dpkg --configure -a

Or when a package script e.g. preinst, posinst, prerm or postrm fails e.g. 
dpkg: error processing distcc (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 distcc 
E: Sub-process /usr/bin/dpkg returned an error code (1)
In this case, to get the package to install/upgrade, there are a ew options and all of them involve getting your hands dirty and diving into the commandline via an editor such as nano or vim or whatever that suits your taste and editing this buggy postinst script with superuser privileges by either

1.
disabling the offending line by preceding "#"
or
2.
forcing it to return success by appending the offending line with "|| true"
or
3.
or open up the offending script file e.g. in this example  a .postinst and append "exit 0" after "set -e"
Save the changes and proceed to configure all partially installed packages with the following command.

sudo dpkg --configure -a or sudo dpkg --configure --pending.

I may be wrong but I doubt any of your GUI package management tools can handle the above errors. And don't forget, I haven't moved on to GRUB2 failing to boot errors yet ;). So rather then wait till the need arise then you go learn or try the commandline why not be prepared and be competently versed in it when the need arises?

---

### Post by spiralx on 2009-12-17
Wow.  Who knew...  OK, I'll take your word for it, even though only about one word in ten of that makes any real sense to me!  Sorry, I'm completely new to this.  I was chuffed to b*ggery just to have your good selves & Synaptic help me through sorting out the...whatever.  

Not sure I actually installed anything that wasn't from Synaptic, though I suspect I pulled down a tar.gz at some point, tried to make it 'go', and gave up in the end...  still, all's well that ends well!

---

### Post by nibirumarduk on 2009-12-17
> **spiralx said:**
> Wow.  Who knew...  OK, I'll take your word for it, even though only about one word in ten of that makes any real sense to me!  Sorry, I'm completely new to this.  I was chuffed to b*ggery just to have your good selves & Synaptic help me through sorting out the...whatever.  

Not sure I actually installed anything that wasn't from Synaptic, though I suspect I pulled down a tar.gz at some point, tried to make it 'go', and gave up in the end...  still, all's well that ends well!


You don't have to take my word for it and neither am i cursing you but I believe you soon run into some of the very issues I identified above.

As for source tarballs, what app was it that you wanted to install? Did you check (type apt-cache search package name or purpose/type of package) if it has already been packaged and can be found in the official Ubuntu repositories or in the ppas ([https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)). Have you search either?

Beware of fork bombs from source packages. Never try to untar, or run make install, etc on tarballs from unknown or untrusted sources unless that is you want a hosed unstall or you want your computer 0wned by e.g. a botnet that is. :shock: :P Always check to see if the program you wanted has already been packaged and is available either in the official Ubuntu repositories or from the ppas.

---


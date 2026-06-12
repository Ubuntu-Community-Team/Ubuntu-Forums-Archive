---
title: "Install extra packages with preseed"
date: 2021-10-13
forum: Installation &amp; Upgrades
---

### Post by jbygden2 on 2021-10-13
Hi!

I have the *exact same* question as this guy here: [https://askubuntu.com/questions/1317770/how-to-install-openssh-server-during-the-install-process](https://askubuntu.com/questions/1317770/how-to-install-openssh-server-during-the-install-process)

How to install extra packages, and I as well would like to install openssh-server (and some more) but neither
```
d-i pkgsel/include string openssh-server
```
nor
```
d-i preseed/late_command string in-target apt-install openssh-server
```
nor
```
ubiquity ubiquity/success_command string in-target apt-install openssh-server
```
installs it.

So, how are one supposed to do to get extra packages installed by preseed?

If the problem is Ubiquity - then how can I use debian-installer instead of Ubiquity?
Is it possible to install Desktop Ubuntu without running the graphical installer?

---

### Post by MAFoElffen on 2021-10-16
I followed this from your other thread: [https://ubuntuforums.org/showthread.php?t=2467323](https://ubuntuforums.org/showthread.php?t=2467323)

As I remember you are using 20.04, and Desktop right? And which flavor of the installer? You want to do automated unattended installations... 

You both mention the (New) Automatic Live Installer system, and the (old) debian-installer system. Then, at the end of this post, you mention if if is "possible to install Desktop Ubuntu without running the graphical installer"... (Whoops)

I think we need to back up to the basics and explanations of those. Neither of these mentioned, new installer system or the new installer system, work with the graphical installer. But rather in a text of of both, where you tell it to use either the user config file for the new installer, or to use the preseed file for the old installer.

That, and you can not mix installer command lines from one installer system to another. The commands above are from the older debian-installer PreSeed file format/type.

Which of the two threads do we need to explain how that works?

---

### Post by jbygden2 on 2021-10-17
> **MAFoElffen said:**
> I followed this from your other thread: [https://ubuntuforums.org/showthread.php?t=2467323](https://ubuntuforums.org/showthread.php?t=2467323)

As I remember you are using 20.04, and Desktop right? And which flavor of the installer? You want to do automated unattended installations... 

You both mention the (New) Automatic Live Installer system, and the (old) debian-installer system. Then, at the end of this post, you mention if if is "possible to install Desktop Ubuntu without running the graphical installer"... (Whoops)

I think we need to back up to the basics and explanations of those. Neither of these mentioned, new installer system or the new installer system, work with the graphical installer. But rather in a text of of both, where you tell it to use either the user config file for the new installer, or to use the preseed file for the old installer.

That, and you can not mix installer command lines from one installer system to another. The commands above are from the older debian-installer PreSeed file format/type.

Which of the two threads do we need to explain how that works?

Oh, you can keep the condescending answers and explanations here in this thread.

I've read through the official documentation here: [https://help.ubuntu.com/lts/installation-guide/amd64/apbs04.html](https://help.ubuntu.com/lts/installation-guide/amd64/apbs04.html)
Could you please point out to me where in that it says I have to use a different installer than what comes with Ubuntu 20.04?
And where in that documentation does it say what installer to use instead.
I'd prefer to install in text-mode, without the graphical installer - although, I'd like it to install the complete Ubuntu desktop and I'd like to be able to add whatever dpkgs I feel like besides what comes with the standard install.
If I have to setup boots/tftp to accomplish that I can do that, but I'd prefer to use a USB-thumbdrive to do the install. And I'd like to do it with as little human intervention as possible. The current preseed-file I use ([https://gist.github.com/jby/a2820aafac806776d346c5eca735d09a](https://gist.github.com/jby/a2820aafac806776d346c5eca735d09a)) only asks for hostname and then presents the User setup dialog. That's a perfect amount of questions. And - no, I don't intend to use a config containing the `r00tme` root-password that's in that gist, other than in my test installations in a VM.

I've utilized the Ubuntu Preseed ISO Generator ([https://github.com/jby/ubuntu-preseed-iso-generator](https://github.com/jby/ubuntu-preseed-iso-generator)) to create the ISO I currently have on a USB-thumbdrive and in my VMWare test-environment.

---

### Post by MAFoElffen on 2021-10-17
I am a bit confused. I have been following your threads and staying out of it, that you were in very good hands. I do not like to step in, if I see someone is already being helped by someone else. I knew that TheFu was very busy yesterday and today.

I apologized that you took anything I said as being condescending in any way. I assure you that my intent was genuinely, and purely in only trying to help you. That misunderstanding and confusion actually hurts my feelings, that you mistook it that way.

Instead of answering you and causing any further confusion, I will contact (my friend) TheFu to help you. (Though I know he is busy with personal things today.) What may help is to post a Pastebin of the PreSeed file, instead of a snippet, so he can debug it, see what section those commands are in and what precedes it. I can read it and make recommendations to the TheFu (if needed) on what i see from that, and debug/test it from my resources.

---

### Post by jbygden2 on 2021-10-17
> **MAFoElffen said:**
> I am a bit confused. I have been following your threads and staying out of it, that you were in very good hands. I do not like to step in, if I see someone is already being helped by someone else. I knew that TheFu was very busy yesterday and today.

I apologized that you took anything I said as being condescending in any way. I assure you that my intent was genuinely, and purely in only trying to help you. That misunderstanding and confusion actually hurts my feelings, that you mistook it that way.

Instead of answering you and causing any further confusion, I will contact (my friend) TheFu to help you. (Though I know he is busy with personal things today.) What may help is to post a Pastebin of the PreSeed file, instead of a snippet, so he can debug it, see what section those commands are in and what precedes it. I can read it and make recommendations to the TheFu (if needed) on what i see from that, and debug/test it from my resources.

I believe you when you say that it wasn't meant to be condescending, sorry.

I did however post the preseed file as a GitHub gist in my previous reply, will that do - or should I find a pastebin somewhere instead?
It's created from the example in the docs ([https://help.ubuntu.com/lts/installation-guide/example-preseed.txt](https://help.ubuntu.com/lts/installation-guide/example-preseed.txt)) with just minor modifications, and the gist is without all comments, as I thought it'd be easier to read without the clutter.

I really appreciate you taking time to assist here. I'm faced with some 40 clients (desktops and, primarily, laptops) that run Fedora today - that I probably have to convert (by re-install) to Ubuntu, and to be able to automate as much as possible would make that task a lesser burden.

---

### Post by MAFoElffen on 2021-10-17
Sorry.

This is what i explained to TheFu what i saw in your original post, which was confusing to me, and thought I should comment on. Please do not take it the wrong way.

You said:
> 
So, how are one supposed to do to get extra packages installed by preseed?


In the 
```

### Package selection
tasksel tasksel/first multiselect ubuntu-desktop 
tasksel tasksel/first multiselect openssh-server
#tasksel tasksel/first multiselect lamp-server, print-server
#tasksel tasksel/first multiselect kubuntu-desktop 

```
At least, that is where I installed that package from usually

Then you said
> If the problem is Ubiquity - then how can I use debian-installer instead of Ubiquity?
This is confusing. Preseed files are for the debian-installer, which "is" Ubiquity... Whereas the yaml config data files are for the Automated Live installer and uses cloud init. 

> Is it possible to install Desktop Ubuntu without running the graphical installer?

This is confusing to me, as the preseed file *will not* work with the graphical installer. At the startof the boot of the ubiquity system, on the first panel, where it has that keyboard/person icon at the bottom, hit the <esc> key. It will boot into the text-mode of the installer. When that gets to the first panel of that, you will notice F-key submenus at the bottom of the screen. 

Press the <F6> key. It will pop up a text mode type menu about at the lower right of the screen. (The same if you were trying to select nomodeset) Arrow down in that menu and select "PreSeed." Then it will look for and use your PreSeed file. ...<Esc><Enter>

I believe that is the missing puzzle piece of your problem. At least from what I saw in what you provided.

---

### Post by jbygden2 on 2021-10-18
I understand your confusion, since I'm equally confused.

You say that Ubiquity ***is*** the debian-installer, however on this page it says: [https://wiki.ubuntu.com/UbiquityAutomation](https://wiki.ubuntu.com/UbiquityAutomation)
```
[COLOR=#333333][FONT=&amp]With respect to automation, [/FONT][/COLOR][ubiquity]("https://wiki.ubuntu.com/Ubiquity")[COLOR=#333333][FONT=&amp], the desktop CD installer, works much in the same way that debian-installer, the alternate CD installer does.[/FONT][/COLOR]
```
That, in combination with the statement (from the same page):
```

[COLOR=#333333][FONT=&amp]Preseeding keys for the following installer components will not be used in Ubiquity, usually because they do not fit with Ubiquity's mode of operation: [/FONT][/COLOR]

[LIST]
[*]netcfg
[*]LVM and RAID partitioning
[*]base-installer
[*]pkgsel/tasksel
[*]finish-install
[/LIST]

```
and, in combination with this, from [https://help.ubuntu.com/lts/installation-guide/amd64/apbs04.html#preseed-pkgsel](https://help.ubuntu.com/lts/installation-guide/amd64/apbs04.html#preseed-pkgsel)
```
[COLOR=#000000][FONT=&amp]If you want to install some individual packages in addition to packages installed by tasks, you can use the parameter [/FONT][/COLOR]pkgsel/include[COLOR=#000000][FONT=&amp]. The value of this parameter can be a list of packages separated by either commas or spaces, which allows it to be used easily on the kernel command line as well.[/FONT][/COLOR]
```
led me to believe that Ubiquity was an Ubuntu-specific installer.
Especially since this works:
```
[COLOR=#000000][FONT=&amp]tasksel tasksel/first multiselect ubuntu-desktop[/FONT][/COLOR]
```
But this doesn't, and, much to my frustration - fails *silently*:
```
[COLOR=#000000][FONT=&amp]d-i pkgsel/include string openssh-server[/FONT][/COLOR]
```
And since Ubuntu strives to be easy I (probably erroneously) then guessed that Ubiquity was the Ubuntu-specific, graphical installer, and that the documentation is too much copied from Debian and not really updated with Ubuntu-specific options.
Hence my question about using the debian-installer instead of Ubiquity, hoping that I'd get a text-only installer that actually would work as indicated in the above mentioned documentation.

---

### Post by jbygden2 on 2021-10-18
I actually started looking at FAI, but couldn't find sufficient documentation on how to customise the install the way I'd like.
That led to me posting "the other thread" where I asked about the recommended way to mass deploy Ubuntu Desktop.
That in turn led me to look at preseed, which ended up in this question.

If you think that FAI might be a better solution for what I'm trying to accomplish, then I'm all ears - but I'd need some pointers to documentation there as well in that case.

---

### Post by jbygden2 on 2021-10-18
Let me specify what I'm trying to achieve here - then you can come up with a tip that you think is the appropriate way to get there.


[LIST]
[*]I have some 40 Fedora clients that probably needs to be converted to Ubuntu (and probably 20.04, because LTS)
[*]I want some type of automatic install, from network or USB stick
[*]I'd like to be able to configure hostname, full disk encryption (cryptsetup) and username/pw for the end user *before* or *during* the installation.
[*]I'd like to be able to add packages to the default desktop installation, and have them be installed during the install (puppet-agent, openssh-server, zsh, vim, git for example)
[*]I'd prefer the install to be text-based, not graphical, if possible (not a deal-breaker) - but it should install the fully graphical Ubuntu desktop.
[/LIST]

---

### Post by jbygden2 on 2021-10-19
Now I've tried
```
tasksel tasksel/first multiselect openssh-server
```
as well, and still no openssh-server installed after install...

---

### Post by MAFoElffen on 2021-10-20
If you look at the installation logs, is it even reading the preseed file? for instance if you did something else in a overtly purposeful off manner,  does it follow the script? That just seems so odd... Because from I hear you saying, it should be working. I think may it might be "me" that is missing or not seeing what is going on... because what you are describing should be working.

Yes, I hear you and I and have to re-look at these details, personally, for my own opensource project, The Ama-gi LiveCD... Where I am facing having come up with my own LiveCD Installation scripts, or using something else, liek SystemBack... where I can just copy/clone, what I have in DEV, and run post-install scripts for the leftover details. So ys, I sort of have a vested interest in this, in a round about way. I can't do that like I have in the past by doing PXE boots, or booting from a USB drive for installations of clients. I have to come up with my own LiveCD ISO. It's a lot easier when you "have" control over what is being installed and you know what it is being installed on. LOL

Is the initial install except for that working? Such as the partitioning and encryption?If it does, then maybe the best would be a post-install script for setting the differing and distinct details, such as a suite of applications being installed, and prompts for filling in the hostname, username and passwords... Or such. One thing that always bugged me was installing a default user and passwords during a mass install, and having them as leftovers on a system, after the deployment... Having to clean those up, later.

Easier? LOL... It just recently got a lot "different. The whole installer system just got changed into sometime else now, and the new one has issues to work through before 22.04.. i'm thinking what I might end up having to do on my own LiveCD project, is having to write my own installation scripts, at that level, but not much is well documented on this new live installer system for that yet...

---

### Post by jbygden2 on 2021-10-20
> **MAFoElffen said:**
> If you look at the installation logs, is it even reading the preseed file? for instance if you did something else in a overtly purposeful off manner,  does it follow the script? That just seems so odd... Because from I hear you saying, it should be working. I think may it might be "me" that is missing or not seeing what is going on... because what you are describing should be working.

I'd say that finding these lines in /var/log/installer/syslog would indicate that it's at least reading the preseed config:
```
Oct 12 18:26:55 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/custom.seed auto=true priority=critical boot=casper automatic-ubiquity quiet splash noprompt noshell ---
Oct 12 18:26:55 ubuntu kernel: [    0.067562] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/custom.seed auto=true priority=critical boot=casper automatic-ubiquity quiet splash noprompt noshell ---
Oct 12 18:26:55 ubuntu kernel: [    0.994447]     file=/cdrom/preseed/custom.seed
Oct 12 18:28:04 ubuntu localechooser: info: debian-installer/locale preseeded to 'en_US' (seen: true)
Oct 12 18:28:38 ubuntu /install.py: keeping packages due to preseeding:
```
However I'd expected to find more lines than only those about preseeding when doing:
```
fgrep preseed /var/log/installer/*
```
But those are the only lines containing 'preseed'...

---

### Post by jbygden2 on 2021-10-20
It **does** setup my sources.list using the Swedish mirror (se.archive.ubuntu.com) that I configure in the preseed, and it uses the 'r00tme' password for root that's also in the preseed.
So - it does do some parts of it.

---

### Post by jbygden2 on 2021-10-20
I'd say that what I have now with the preseed, where the installer asks me for hostname, luks password and presents me with a "Create User" dialog is as close to perfect for my needs as I could hope to get. I guess I have to finish the setup with puppet, but I'd really like the preseed to install some extra packages, including puppet-agent.

---

### Post by jbygden2 on 2021-10-21
> **jbygden2 said:**
> It **does** setup my sources.list using the Swedish mirror (se.archive.ubuntu.com) that I configure in the preseed, and it uses the 'r00tme' password for root that's also in the preseed.
So - it does do some parts of it.
Hmm, I was wrong.

It doesn't setup the Swedish mirror and it doesn't set the root password.

It **does** however follow the preseed when it comes to volume setup:
```
d-i partman-auto/method string crypto
```
will ask for, and use, a luks password, whereas
```
d-i partman-auto/method string lvm
```
does not.

I'm really confused by this now...:(

---

### Post by jbygden2 on 2021-10-21
It's also "respecting" the setting for hostname:
```
[COLOR=#24292F][FONT=ui-monospace]d-i netcfg/get_hostname string unassigned-hostname[/FONT][/COLOR]
```

---

### Post by jbygden2 on 2021-10-21
It's definitely reading the preseed-file.
I tested to put my preseed.cfg on a web server and pointed the boot to it, and it's reflected in /var/log/installer/syslog after setup that it's read that file.

I'm getting more and more confused here...

---

### Post by jbygden2 on 2021-10-24
So, is [autoinstall]("https://ubuntu.com/server/docs/install/autoinstall") the way to go instead? Or is that 'server only', and will only confuse me even more?
I've now read on mulitple places that as of 20.04 the 'old' debian-installer is no longer in use (or even supported) for installing...

---

### Post by jbygden2 on 2021-10-24
Found the [Kickseed]("https://launchpad.net/kickseed") stuff on Launchpad, which apparently was supposed to be used as a preseed replacement for kickstart, but it's not been touched since February 2014 - so I'm guessing it's not really relevant any more...

---

### Post by jbygden2 on 2021-10-24
Is there really **no-one** that has a *working* config for mass deployment (not really that 'mass' either) of Ubuntu hosts - other than imaging, which I'd prefer not to use?

---

### Post by jbygden2 on 2021-10-24
I'm starting to think I'd just have to accept the fact that I'll just have to go with what I have at the moment.
Which is a *partly working* preseed for a basic install.
And then install puppet or ansible and finish the setup that way...

---

### Post by MAFoElffen on 2021-10-24
Sorry. Been overwhelmed with work related. Haven't even had time to spend on my own projects. Some of these things you are going through, are relevant to what I need to go through with one of my own projects (The Ama-Gi Project). In that I need to produce LiveCD ISO's that have the option to install as a derivative Distro. The last time I created a LiveCD was over 8 years ago, and many things have change since then.

Your past few posts... Here are some things that had been running around in my head. About just using a Server Install, and installing the Desktop on it... Let me back up a bit to answer some of your questions.

Yes, The 20.04.x Server Install is the new Live Installer. The 20.04.x Desktop is the old, and now outdated installer. Supposedly, by 22.04, the Desktop Edition with be fully on the Live Installer. I had heard that Desktop first uses the new Live Installer in 21.10, but honestly. IDK. But yes, the older installer is out. So starting something new, for it is... Well... 

Without going into detail, we are forced to use the Live Installer. It is here and not going away. It is not well documented yet (because it is new). We are finding a lot wrong with it. But with the "yaml" file structure, it does have a lot of potential for trying to install a systemd based system. If you search on "LHammonds", he has a thread, trying to keep track of and on top on trying to deal with the problems and limitations of, as well as the work-arounds we have found for it.

20.04.1 Server was the first ISO to include use the new Live Installer... But for you, has some oddities about getting LUKS to work as "full disk" encryption. Even if you install it manually.

As you mentioned with puppet and ansible play books, I had come up with my own post-installation scripts to deal with things in the meantime. I, myself, am still trying to learn the new Live Install automatic install system and how to use it. I cannot say I fully understand it. Honestly, it feels like I am stumbling around with everyone else on it.

---

### Post by jbygden2 on 2021-10-24
> **MAFoElffen said:**
> Yes, The 20.04.x Server Install is the new Live Installer. The 20.04.x Desktop is the old, and now outdated installer. Supposedly, by 22.04, the Desktop Edition with be fully on the Live Installer. I had heard that Desktop first uses the new Live Installer in 21.10, but honestly. IDK. But yes, the older installer is out. So starting something new, for it is... Well... 

I haven't looked at the Server Install, since I'm not installing servers - I'm updating desktop clients from Fedora. And I'm bound by requirements to look at the LTS, and hence haven't looked at anything newer than 20.04.

---

### Post by jbygden2 on 2021-10-27
I'm now at a state where I have created an ansible-playbook to do most of the config after installation, however - to be able to run it 'openssh-server' needs to be installed, and I'd really like that to be installed during the initial install.
Do you have **ANY** tips on how I might accomplish that?

---

### Post by ActionParsnip on 2021-10-27
Could use chef or puppet to deploy things too

---

### Post by jbygden2 on 2021-10-27
> **ActionParsnip said:**
> Could use chef or puppet to deploy things too
Just like ansible, that I've chosen this time, both of those require components to be installed ***before*** deploying anything with them - and my main problem is the inability to install extra pkgs during install...

If I just could get 'openssh-server' installed by the main installer - I'd have most of my problems solved...

---

### Post by MAFoElffen on 2021-10-27
Like I started tp hint at and suggest... Maybe install from a Server Edition ISO. That is an ISO, histtorically, where you do preseeds and autoinstalls. More frequently than Desktop.

On Server Edition, you can go full or minimal. Minimal would be core services:

Package openssh-server is a default installation application... Add package ubuntu-desktop. I install from that ISO because of that one difference. From that ISO, I can deploy any flavor or variant. And if it is going to be visualized, I can use cloud init, to help it along.

This is what I do with my own Support LiveCD, then install packages and configs from there. Do not think of "Server" as just being server, but as a Linux core system instance, with the potential and waiting to be "something". 

The only thing peculiar about it, in the transforming of Server ISO installs to Desktop, after the ubuntu-desktop package is installed... Is to tell it to use Network Manager, instead of NetPlan, as the networking managing service. So that users can manage nw connections graphically. But that is just one extra command after that package is installed. 

To me, it is like using the old "Ubuntu Minimal ISO", where you installed a core, then made it into something. The Minimal ISO does not exist anymore, but there is still the Net Install and Server ISO's that do the same functionally.

There is one command to transform a Desktop to a Server, and 1 (+1, the additional network config related command I noted above) to turn server into a Desktop Edition. But doing that, openssh-server stays there.

---

### Post by tea for one on 2021-10-27
> **jbygden2 said:**
> I'm now at a state where I have created an ansible-playbook to do most of the config after installation, however - to be able to run it 'openssh-server' needs to be installed, and I'd really like that to be installed during the initial install.
Do you have **ANY** tips on how I might accomplish that?

Perhaps this application will help you to include [COLOR="#0000FF"]openssh-server[/COLOR] in your source ISO?

[https://launchpad.net/cubic](https://launchpad.net/cubic)

---

### Post by MAFoElffen on 2021-10-27
@Tea For One

I did a quick search on that:
[https://www.linuxuprising.com/2018/07/how-to-customize-ubuntu-or-linux-mint.html](https://www.linuxuprising.com/2018/07/how-to-customize-ubuntu-or-linux-mint.html)
[https://ubunlog.com/en/cubic-iso-personalizada-ubuntu/](https://ubunlog.com/en/cubic-iso-personalizada-ubuntu/)
[https://ostechnix.com/how-to-create-a-custom-ubuntu-live-iso-image-with-cubic/](https://ostechnix.com/how-to-create-a-custom-ubuntu-live-iso-image-with-cubic/)

I think that will also help me with the Ama-gi Project LiveCD. Thank you.

Started reading the walk throughs... Lots of CLI manual work for me. CLI inside of it's chroot inside of it. Still a possibility for me. May be a problem for the OP.

Another possible for him though is what I originally was going to use for the Ama-Gi project, which is SystemBack 2.0. Create one system (I did in virtual), then create a LiveCD out that system using SystemBack... Which in turn, the LiveCD has an install, to install that to Live metal. This is my fallback for my project. My project being that way, I can install, debug and test everything on a running, live system, to see what is happening. And do it on both Legacy and UEFI.
[https://sourceforge.net/projects/systemback-2021/](https://sourceforge.net/projects/systemback-2021/)

---

### Post by jbygden2 on 2021-10-28
I'm trying out [Cubic]("https://launchpad.net/cubic") to build a customized install ISO now

---

### Post by jbygden2 on 2021-10-28
> **jbygden2 said:**
> I'm trying out [Cubic]("https://launchpad.net/cubic") to build a customized install ISO now
Nope - not even with the 'openssh-server' added to the standard install... :(

How the hell can this be this difficult?

---

### Post by jbygden2 on 2021-10-28
> **jbygden2 said:**
> Nope - not even with the 'openssh-server' added to the standard install... :(

Ok, it's just a fancy GUI to create a preseed install - which takes me back to [post #1]("https://ubuntuforums.org/showthread.php?t=2467953") in this thread... :(
So, I'm just back to where I started...

---

### Post by jbygden2 on 2021-10-28
> **tea for one said:**
> Perhaps this application will help you to include [COLOR=#0000FF]openssh-server[/COLOR] in your source ISO?

[https://launchpad.net/cubic](https://launchpad.net/cubic)

Cubic is just a fancy GUI to create a preseed install -> goto [post #1]("https://ubuntuforums.org/showthread.php?t=2467953&p=14062847&viewfull=1#post14062847") in this thread

---

### Post by jbygden2 on 2021-10-28
> **MAFoElffen said:**
> @Tea For One

I did a quick search on that:
[https://www.linuxuprising.com/2018/07/how-to-customize-ubuntu-or-linux-mint.html](https://www.linuxuprising.com/2018/07/how-to-customize-ubuntu-or-linux-mint.html)
[https://ubunlog.com/en/cubic-iso-personalizada-ubuntu/](https://ubunlog.com/en/cubic-iso-personalizada-ubuntu/)
[https://ostechnix.com/how-to-create-a-custom-ubuntu-live-iso-image-with-cubic/](https://ostechnix.com/how-to-create-a-custom-ubuntu-live-iso-image-with-cubic/)

I think that will also help me with the Ama-gi Project LiveCD. Thank you.

Started reading the walk throughs... Lots of CLI manual work for me. CLI inside of it's chroot inside of it. Still a possibility for me. May be a problem for the OP.

Another possible for him though is what I originally was going to use for the Ama-Gi project, which is SystemBack 2.0. Create one system (I did in virtual), then create a LiveCD out that system using SystemBack... Which in turn, the LiveCD has an install, to install that to Live metal. This is my fallback for my project. My project being that way, I can install, debug and test everything on a running, live system, to see what is happening. And do it on both Legacy and UEFI.
[https://sourceforge.net/projects/systemback-2021/](https://sourceforge.net/projects/systemback-2021/)

Don't hold your breath @MAFoElffen - Cubic is just a fancy GUI to create a preseed install -> goto [post #1]("https://ubuntuforums.org/showthread.php?t=2467953") of this thread... :(

---

### Post by jbygden2 on 2021-10-28
> **MAFoElffen said:**
> Like I started tp hint at and suggest... Maybe install from a Server Edition ISO. That is an ISO, histtorically, where you do preseeds and autoinstalls. More frequently than Desktop.

On Server Edition, you can go full or minimal. Minimal would be core services:

Package openssh-server is a default installation application... Add package ubuntu-desktop. I install from that ISO because of that one difference. From that ISO, I can deploy any flavor or variant. And if it is going to be visualized, I can use cloud init, to help it along.

This is what I do with my own Support LiveCD, then install packages and configs from there. Do not think of "Server" as just being server, but as a Linux core system instance, with the potential and waiting to be "something". 

The only thing peculiar about it, in the transforming of Server ISO installs to Desktop, after the ubuntu-desktop package is installed... Is to tell it to use Network Manager, instead of NetPlan, as the networking managing service. So that users can manage nw connections graphically. But that is just one extra command after that package is installed. 

To me, it is like using the old "Ubuntu Minimal ISO", where you installed a core, then made it into something. The Minimal ISO does not exist anymore, but there is still the Net Install and Server ISO's that do the same functionally.

There is one command to transform a Desktop to a Server, and 1 (+1, the additional network config related command I noted above) to turn server into a Desktop Edition. But doing that, openssh-server stays there.

My next test: [https://askubuntu.com/questions/1233454/how-to-preseed-ubuntu-20-04-desktop](https://askubuntu.com/questions/1233454/how-to-preseed-ubuntu-20-04-desktop) 
Seems to be more or less the same that you suggests above...

---

### Post by tea for one on 2021-10-28
> **jbygden2 said:**
> Nope - not even with the 'openssh-server' added to the standard install.

Just curious..........

Did you manage to install openssh-server using Cubic and create a new ISO?

The intention of recommending Cubic was to try and help with your question in post no. 24
> I'm now at a state where I have created an ansible-playbook to do most of the config after installation, however - to be able to run it 'openssh-server' needs to be installed, and I'd really like that to be installed during the initial install.
Do you have ANY tips on how I might accomplish that? 

---

### Post by jbygden2 on 2021-10-28
> **jbygden2 said:**
> My next test: [https://askubuntu.com/questions/1233454/how-to-preseed-ubuntu-20-04-desktop](https://askubuntu.com/questions/1233454/how-to-preseed-ubuntu-20-04-desktop) 
Seems to be more or less the same that you suggests above...

So, I've now tried using the server image and autoinstall (cloud-init) config, trying out the script from here: [https://github.com/covertsh/ubuntu-autoinstall-generator](https://github.com/covertsh/ubuntu-autoinstall-generator)

But - alas:
```
waiting for cloud-init...
finish: subiquity/Package/load_autoinstall_data: 'ubuntu-desktop' is not of type 'array'


Failed validating 'type' in schema:
    {'items': {'type: 'string'}, 'type': 'array'}
    
On instance:
    'ubuntu-desktop'
An error occurred. Press enter to start shell

```
At least I've now found a way found **a** ubuntu installer that actually *does read* a pre-config-file, albeit giving an error. I still view this as a **huge**&#8203; success... :(

---

### Post by jbygden2 on 2021-10-28
> **tea for one said:**
> Just curious..........

Did you manage to install openssh-server using Cubic and create a new ISO?

The intention of recommending Cubic was to try and help with your question in post no. 24

No, as I answered to your post - Cubic is just a fancy GUI to configure preseed, which I've already tried and which led to the creation of this thread in the first place.

I added openssh-server to the install in Cubic and built the ISO - and it behaves just like the manually built. The 'openssh-server' is present in the preseed-file, but ignored by the installer.

---

### Post by jbygden2 on 2021-10-28
Next I'm watching this: [h=1][Getting Started with cloud-init]("https://youtu.be/exeuvgPxd-E")[/h]And see where to go from there.

---

### Post by jbygden2 on 2021-10-28
> **jbygden2 said:**
> Next I'm watching this: **[Getting Started with cloud-init]("https://youtu.be/exeuvgPxd-E")**

And see where to go from there.

Hmm, ok, so now I know how to edit `/etc/cloud/cloud.cfg` but not much else...

---

### Post by jbygden2 on 2021-10-28
> **jbygden2 said:**
> So, I've now tried using the server image and autoinstall (cloud-init) config, trying out the script from here: [https://github.com/covertsh/ubuntu-autoinstall-generator](https://github.com/covertsh/ubuntu-autoinstall-generator)

But - alas:
```
waiting for cloud-init...
finish: subiquity/Package/load_autoinstall_data: 'ubuntu-desktop' is not of type 'array'


Failed validating 'type' in schema:
    {'items': {'type: 'string'}, 'type': 'array'}
    
On instance:
    'ubuntu-desktop'
An error occurred. Press enter to start shell

```
At least I've now found a way found **a** ubuntu installer that actually *does read* a pre-config-file, albeit giving an error. I still view this as a **huge**&#8203; success... :(

OK - this was caused by a typo by me, solved now!

Now I finally have something to build from... :)

---

### Post by jbygden2 on 2021-10-28
This article was the solution in the end: [https://www.pugetsystems.com/labs/hpc/How-To-Make-Ubuntu-Autoinstall-ISO-with-Cloud-init-2213/](https://www.pugetsystems.com/labs/hpc/How-To-Make-Ubuntu-Autoinstall-ISO-with-Cloud-init-2213/)

---

### Post by MAFoElffen on 2021-10-31
Sorry for my absence. New job, with two other technicians on vacation, so I was getting many extra service calls from three counties.

Good to hear and know. They are local to me and I used to read a lot of his articles...

---

### Post by jbygden2 on 2021-11-01
> **MAFoElffen said:**
> Sorry for my absence. New job, with two other technicians on vacation, so I was getting many extra service calls from three counties.

Good to hear and know. They are local to me and I used to read a lot of his articles...

Still, though - if you have any input in it - the documentation needs updating on the issue...

---

### Post by MAFoElffen on 2021-11-02
LOL. 

The biggest challenge for people is not just learning the new directives, options and recipes, but that people are not used to indent/space conventions of Yaml. Yaml files and the conventions of are everywhere now, in systemd... Like for networkd. One extra space... Or a tab somewhere instead of spaces, and it fails. It might look visually correct, and be wrong. Debugging other people's code gets to be a challenge, when they post it online, instead of in a file.  I have a background in Python... So maybe just more used to that than a few. 

Most of what I've read, and tried to use to get an understanding of how cloud-init works, is from a different perspective (at least for me) than the Canonical Doc's... I think the more complete Doc's are from Amazon EC2 AWS::CloudFormation::Init, the Microsoft Azure (cloud-init support for virtual machines), and RedHat Atomic Host (setup for cloud-init) documentation. There they are explaining this is how you do it, to their customers. I think that a lot of Azure's understanding, came from Canonical... But Canonical's own Doc's on it seem very sparse. If they are there, they just are not as visual or accessible to find.

---

### Post by jbygden2 on 2021-11-03
> **MAFoElffen said:**
> LOL. 

The biggest challenge for people is not just learning the new directives, options and recipes, but that people are not used to indent/space conventions of Yaml. Yaml files and the conventions of are everywhere now, in systemd... Like for networkd. One extra space... Or a tab somewhere instead of spaces, and it fails. It might look visually correct, and be wrong. Debugging other people's code gets to be a challenge, when they post it online, instead of in a file.  I have a background in Python... So maybe just more used to that than a few. 

Most of what I've read, and tried to use to get an understanding of how cloud-init works, is from a different perspective (at least for me) than the Canonical Doc's... I think the more complete Doc's are from Amazon EC2 AWS::CloudFormation::Init, the Microsoft Azure (cloud-init support for virtual machines), and RedHat Atomic Host (setup for cloud-init) documentation. There they are explaining this is how you do it, to their customers. I think that a lot of Azure's understanding, came from Canonical... But Canonical's own Doc's on it seem very sparse. If they are there, they just are not as visual or accessible to find.
I'm more thinking of at least mentioning the fact that preseed stopped working as of 20.04.

---

### Post by MAFoElffen on 2021-11-03
Yes, but for Desktop Edition... They started testing the new live installer for Desktop 21.10 in the Dev cycle back in June - July 2021. I haven't installed Desktop 21.10 "from ISO", But I think the plan was for it to be on that new live installer, and the problems worked out before 22.04.

But the thing is, they were testing the installer itself. Not sure if anyone was testing the auto-installer part of that for the Desktop Edition. That is usually just us server guys who use that part.

I know on the Server side of that, We have a thread miles longs on the problems with the Server Editon Live Installer... and work-around's for.

---

### Post by jbygden2 on 2021-11-04
> **MAFoElffen said:**
> Yes, but for Desktop Edition... They started testing the new live installer for Desktop 21.10 in the Dev cycle back in June - July 2021. I haven't installed Desktop 21.10 "from ISO", But I think the plan was for it to be on that new live installer, and the problems worked out before 22.04.

But the thing is, they were testing the installer itself. Not sure if anyone was testing the auto-installer part of that for the Desktop Edition. That is usually just us server guys who use that part.

I know on the Server side of that, We have a thread miles longs on the problems with the Server Editon Live Installer... and work-around's for.

Yet, this is still part of the official documentation: [https://help.ubuntu.com/lts/installation-guide/amd64/apb.html](https://help.ubuntu.com/lts/installation-guide/amd64/apb.html)
And hardly any of it is applicable to 20.04 today...

---

### Post by jbygden2 on 2021-11-17
However - switching to Debian solves all my problems, there it just works...

---


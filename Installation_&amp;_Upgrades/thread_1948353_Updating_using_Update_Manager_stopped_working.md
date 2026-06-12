---
title: "Updating using Update Manager stopped working?"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by jorritTyb on 2012-03-28
Hi all,

I have been using Ubuntu 11.10 for a while and have updated it regularly using the Update Manager. Today I boot up the machine and it tells me there are 15 updates. So I fire up the Update Manager and press 'Install Updates' but nothing happens. This has always worked before but now I can't update anymore it seems. Additionally the 'Check' button takes a HUGE time to get all packages that need updating. This is also usually a very fast operation.

Any idea what's wrong and how I can fix this? I don't see any error messages or something.

Greetings and thanks,

---

### Post by zvacet on 2012-03-28
Well, I don´t know jow to fix update manager,but you can get updates via **synaptic >refresh>mark all updates.**To get faster download try to change server and see if that help.

---

### Post by garvinrick4 on 2012-03-28
I shutting down and a reboot usually fixes most:
If not try terminal and see if get any errors:
Copy and paste this in terminal. If any errors report back:
```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by jorritTyb on 2012-03-28
Ok:

a) Rebooting did *not* solve the problem.
b) I did the manual update commands and that seemed to have worked. I got no errors and at boot time the system doesn't say there are packages to update.

However!

The graphical system update tool still shows the original packages (that have been updated by now) and fails to do anything when I press 'Install Updates'.

Seems that tool got broken somehow.

Any clues?

---

### Post by zvacet on 2012-03-28
If package manager show there is some packages for update you have to be able to see them when running

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jorritTyb on 2012-03-28
Hmm seems doing these commands again brought in other updates. Weird...

Any way the tool is no longer responding now when I select 'Check'. Things only got worse :-/

---

### Post by jorritTyb on 2012-03-28
No matter what I do the Update Manager keeps showing a few packages. The packages that it lists are related to a new linux kernel. They are selected but pressing 'Install Updates' still doesn't work. Doing the sudo update/upgrade commands doesn't do anything (besides checking) anymore. So I believe there is now nothing to update but the Update Manager is somehow convinced that there is something that should be updated.

Can I clear some cache or something to start clean?

Greetings,

---

### Post by Old_Grey_Wolf on 2012-03-28
> **jorritTyb said:**
> Hmm seems doing these commands again brought in other updates. Weird...

Any way the tool is no longer responding now when I select 'Check'. Things only got worse :-/

You need to execute these commands in a terminal and copy-paste the errors you get to this thread. 
```
sudo apt-get update
sudo apt-get upgrade
```

That is what Garvinrick4 and zvacet were asking you to do. Without the errors it is difficult for anyone to help you. Anyone trying to help would be guessing about the underlying problem without the errors asked for previously.

---

### Post by cortman on 2012-03-28
This sounds like it may just call for a reinstallation of update manager-

```
sudo apt-get remove update-manager
sudo apt-get install update-manager
```

---

### Post by jorritTyb on 2012-03-29
> **Old_Gray_Wolf said:**
> You need to execute these commands in a terminal and copy-paste the errors you get to this thread. 
```
sudo apt-get update
sudo apt-get upgrade
```

That is what Garvinrick4 and zvacet were asking you to do. Without the errors it is difficult for anyone to help you. Anyone trying to help would be guessing about the underlying problem without the errors asked for previously.

Yes, I agree. The only problem is that these commands don't give me any errors. At least I don't see any. I can give you the total output if you want though. It is a bit much. At the moment I'm at work but this evening I can send over the output.

Greetings,

---

### Post by jorritTyb on 2012-03-29
Ok, here is the output of both update and upgrade:

apt-get update:

```

Ign http://archive.canonical.com natty InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease
Hit http://archive.canonical.com natty Release.gpg
Ign http://be.archive.ubuntu.com oneiric InRelease
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Hit http://security.ubuntu.com oneiric-security Release.gpg
Hit http://archive.canonical.com natty Release
Hit http://extras.ubuntu.com oneiric Release
Ign http://be.archive.ubuntu.com oneiric-updates InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Hit http://security.ubuntu.com oneiric-security Release
Hit http://archive.canonical.com natty/partner Sources
Hit http://extras.ubuntu.com oneiric/main Sources
Ign http://be.archive.ubuntu.com oneiric-backports InRelease
Hit http://security.ubuntu.com oneiric-security/main Sources
Hit http://archive.canonical.com natty/partner amd64 Packages
Hit http://archive.canonical.com natty/partner i386 Packages
Hit http://extras.ubuntu.com oneiric/main amd64 Packages
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://ppa.launchpad.net oneiric Release.gpg
Ign http://archive.canonical.com natty/partner TranslationIndex
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://be.archive.ubuntu.com oneiric Release.gpg
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://ppa.launchpad.net oneiric Release
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Get:2 http://be.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://be.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://be.archive.ubuntu.com oneiric Release
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://ppa.launchpad.net oneiric/main amd64 Packages
Hit http://ppa.launchpad.net oneiric/main i386 Packages
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Get:3 http://be.archive.ubuntu.com oneiric-updates Release [40.8 kB]
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Ign http://archive.canonical.com natty/partner Translation-en
Hit http://be.archive.ubuntu.com oneiric-backports Release
Hit http://be.archive.ubuntu.com oneiric/main Sources
Hit http://be.archive.ubuntu.com oneiric/restricted Sources
Hit http://be.archive.ubuntu.com oneiric/universe Sources
Hit http://be.archive.ubuntu.com oneiric/multiverse Sources
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Hit http://be.archive.ubuntu.com oneiric/main amd64 Packages
Hit http://be.archive.ubuntu.com oneiric/restricted amd64 Packages
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://be.archive.ubuntu.com oneiric/universe amd64 Packages
Hit http://be.archive.ubuntu.com oneiric/multiverse amd64 Packages
Hit http://be.archive.ubuntu.com oneiric/main i386 Packages
Hit http://be.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://be.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://be.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://be.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://be.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://be.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://be.archive.ubuntu.com oneiric/universe TranslationIndex
Get:4 http://be.archive.ubuntu.com oneiric-updates/main Sources [132 kB]
Get:5 http://be.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:6 http://be.archive.ubuntu.com oneiric-updates/universe Sources [48.8 kB]
Get:7 http://be.archive.ubuntu.com oneiric-updates/multiverse Sources [3,661 B]
Get:8 http://be.archive.ubuntu.com oneiric-updates/main amd64 Packages [308 kB]
Get:9 http://be.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]
Get:10 http://be.archive.ubuntu.com oneiric-updates/universe amd64 Packages [104 kB]
Get:11 http://be.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,210 B]
Get:12 http://be.archive.ubuntu.com oneiric-updates/main i386 Packages [308 kB]
Get:13 http://be.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:14 http://be.archive.ubuntu.com oneiric-updates/universe i386 Packages [105 kB]
Get:15 http://be.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,356 B]
Get:16 http://be.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:17 http://be.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:18 http://be.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:19 http://be.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://be.archive.ubuntu.com oneiric-backports/main amd64 Packages
Hit http://be.archive.ubuntu.com oneiric-backports/restricted amd64 Packages
Hit http://be.archive.ubuntu.com oneiric-backports/universe amd64 Packages
Hit http://be.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
Hit http://be.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://be.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://be.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://be.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://be.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://be.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://be.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://be.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://be.archive.ubuntu.com oneiric/main Translation-en
Hit http://be.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://be.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://be.archive.ubuntu.com oneiric/universe Translation-en
Get:20 http://be.archive.ubuntu.com oneiric-updates/main Translation-en [143 kB]
Hit http://be.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://be.archive.ubuntu.com oneiric-updates/restricted Translation-en
Get:21 http://be.archive.ubuntu.com oneiric-updates/universe Translation-en [62.9 kB]
Hit http://be.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://be.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://be.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://be.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://dl.google.com stable InRelease
Get:22 http://dl.google.com stable Release.gpg [198 B]
Get:23 http://dl.google.com stable Release [1,338 B]
Get:24 http://dl.google.com stable/main amd64 Packages [469 B]
Get:25 http://dl.google.com stable/main i386 Packages [464 B]
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Fetched 1,278 kB in 1min 56s (10.9 kB/s)
Reading package lists...

```


apt-get upgrade:

```

Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.

```

The Software Update tool still claims there are six packages to update and still fails to update them.

Greetings,

---

### Post by jorritTyb on 2012-03-29
> **cortman said:**
> This sounds like it may just call for a reinstallation of update manager-

```
sudo apt-get remove update-manager
sudo apt-get install update-manager
```

Unfortunately this didn't fix things. The only thing that happened is that it claimed that the computer needed a restart but the 'Restart Now' button wasn't working. I restarted manually but nothing happens. According to the software updater there are still six updates waiting to happen but it fails to update them.

Greetings,

---

### Post by cortman on 2012-03-29
That's very strange. Have you tried running

```
sudo apt-get autoclean
```

---

### Post by jorritTyb on 2012-03-29
> **cortman said:**
> That's very strange. Have you tried running

```
sudo apt-get autoclean
```

That didn't help.

To make things worse. I discovered that Ubuntu Software Center also stopped working. I can browse, ask information but the 'Install' button for installing new stuff doesn't do anything at all.

It really looks like the same problem. Somehow all buttons with the label 'Install' on it stopped working :-/

Any ideas?

---

### Post by cortman on 2012-03-29
Your apt-get seems to be working fine; but the GUI front ends are falling apart.
I've helped many people fix the software center by uninstalling and reinstalling. I hope it doesn't seem like trying the same thing twice and hoping for different results, but you might try uninstalling USC and the update manager, then reinstalling in that order.

```
sudo apt-get purge software-center
sudo apt-get purge update-manager
```

Then reinstalling them.
If this doesn't work, I'm not sure what else will. You'll still be able to update and install software using the command line, so you're not totally stuck.

---

### Post by jorritTyb on 2012-03-29
Ok I found something. I ran software-center from the shell to see if any errors appear on the output when I press 'Install'. And this is what appears:

```

2012-03-29 20:05:31,138 - softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.58'}): org.debian.apt.install-or-remove-packages

```

I don't know what this means exactly but this appears every time I press the Install button.

Greetings,

---

### Post by jorritTyb on 2012-03-29
> **cortman said:**
> Your apt-get seems to be working fine; but the GUI front ends are falling apart.
I've helped many people fix the software center by uninstalling and reinstalling. I hope it doesn't seem like trying the same thing twice and hoping for different results, but you might try uninstalling USC and the update manager, then reinstalling in that order.

```
sudo apt-get purge software-center
sudo apt-get purge update-manager
```

Then reinstalling them.
If this doesn't work, I'm not sure what else will. You'll still be able to update and install software using the command line, so you're not totally stuck.

I'm sorry to say that this doesn't help. I'm still getting the same error.

Greetings,

---

### Post by Old_Grey_Wolf on 2012-03-29
I see from the output of the sudo apt-get upgrade command that you have a kernel update pending. To upgrade the kernel enter these commands```
sudo apt-get update
sudo apt-get dist-upgrade
```

It may clear out some or all of the updates in the list.

---

### Post by jorritTyb on 2012-03-30
> **Old_Gray_Wolf said:**
> I see from the output of the sudo apt-get upgrade command that you have a kernel update pending. To upgrade the kernel enter these commands```
sudo apt-get update
sudo apt-get dist-upgrade
```

It may clear out some or all of the updates in the list.

It did indeed. But since after this the software updater no longer shows any updates I cannot confirm if the 'Install' button works or not. However. The 'Install' button of the Ubuntu Software Center is still broken after this update.

Greetings and thanks for all the help so far,

---

### Post by zvacet on 2012-03-30
I see tha you have mixed repos.

>  [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Remove natty repo from your source list and then 

```
sudo apt-get update
```

Maybe this will not solve your problem,but it will keep your source list clean.

---

### Post by matt_symes on 2012-03-30
Hi

From the terminal does this work ?

```
gksudo update-manager
```

Also what is the output of this command ?

```
cat /usr/share/polkit-1/actions/org.freedesktop.policykit.policy
```

Kind regards

---

### Post by desi on 2012-03-30
Plese see my responses below:

> **matt_symes said:**
> Hi

From the terminal does this work ?

```
gksudo update-manager
```

Nothing happens after it asks for the password. A window appears and disappears in a rfaction of a second

Also what is the output of this command ?

```
cat /usr/share/polkit-1/actions/org.freedesktop.policykit.policy
```

Here it is:
drbhat@doctoroffice:~$ cat /usr/share/polkit-1/actions/org.freedesktop.policykit.policy
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>
  <vendor>The PolicyKit Project</vendor>
  <vendor_url>http://hal.freedesktop.org/docs/PolicyKit/</vendor_url>

  <action id="org.freedesktop.policykit.exec">
    <description>Run programs as another user</description>
    <description xml:lang="da">Kør et program som en anden bruger</description>
    <message>Authentication is required to run a program as another user</message>
    <message xml:lang="da">Autorisering er påkrævet for at afvikle et program som en anden bruger</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.policykit.lockdown">
    <description>Configure lock down for an action</description>
    <description xml:lang="da">Konfigurer lock down for en action</description>
    <message>Authentication is required to configure lock down policy</message>
    <message xml:lang="da">Autorisering er påkrævet for at konfigurer lock down</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/pklalockdown</annotate>
  </action>


Kind regards

---

### Post by jorritTyb on 2012-03-30
> **matt_symes said:**
> Hi

From the terminal does this work ?

```
gksudo update-manager
```


Yes it just opens the update-manager. Can't check if the Install button works now since my system is up-to-date.


> 
Also what is the output of this command ?

```
cat /usr/share/polkit-1/actions/org.freedesktop.policykit.policy
```

Kind regards

The output is:

```

<?xml version="2.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>
  <vendor>The PolicyKit Project</vendor>
  <vendor_url>http://hal.freedesktop.org/docs/PolicyKit/</vendor_url>

  <action id="org.freedesktop.policykit.exec">
    <description>Run programs as another user</description>
    <description xml:lang="da">Kør et program som en anden bruger</description>
    <message>Authentication is required to run a program as another user</message>
    <message xml:lang="da">Autorisering er påkrævet for at afvikle et program som en anden bruger</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.policykit.lockdown">
    <description>Configure lock down for an action</description>
    <description xml:lang="da">Konfigurer lock down for en action</description>
    <message>Authentication is required to configure lock down policy</message>
    <message xml:lang="da">Autorisering er påkrævet for at konfigurer lock down</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/pklalockdown</annotate>
  </action>
</policyconfig>

```

Thanks

---

### Post by Old_Grey_Wolf on 2012-03-30
Does the install button work if you start the software center with the command line? ```
gksu software-center
```

---

### Post by jorritTyb on 2012-03-30
> **Old_Gray_Wolf said:**
> Does the install button work if you start the software center with the command line? ```
gksu software-center
```

Hmm, yes that works but that is not the same software center as the one that I was using which is called 'Ubunutu Software Center'. At least it looks totally different in user interface.

But yes, with that I can install software correctly. To confirm I just tried ubuntu software center again and that one still doesn't work.

Greetings,

---

### Post by Old_Grey_Wolf on 2012-03-30
Have you changed your password recently?

---

### Post by jorritTyb on 2012-03-30
> **Old_Gray_Wolf said:**
> Have you changed your password recently?

Nope. Haven't changed it in months.

Greetings,

---

### Post by Old_Grey_Wolf on 2012-03-30
Try to rename ~/.cache/software-center to something else and try again.

```
mv ~/.cache/software-center ~/.cache/software-center.old
```

---

### Post by jorritTyb on 2012-03-30
> **Old_Gray_Wolf said:**
> Try to rename ~/.cache/software-center to something else and try again.

```
mv ~/.cache/software-center ~/.cache/software-center.old
```

Nope :-(  Same result after moving this.

Greetings and thanks for the stream of help.

---

### Post by Old_Grey_Wolf on 2012-03-30
I have run out of ideas :(

At least with the commands "gksudo update-manager" and "gksu software-center" you can get by until someone comes along with the solution.

It appears that update-manager and software-center don't allow you to have sudo privileges unless you start them from the command line. 

I was thinking that changing your password may have caused a problem somewhere; however, you haven't changed it recently.

---

### Post by matt_symes on 2012-03-30
Hi

> Hmm, yes that works but that is not the same software center as the one that I was using which is called 'Ubunutu Software Center'. At least it looks totally different in user interface.

But yes, with that I can install software correctly. To confirm I just tried ubuntu software center again and that one still doesn't work.

I don't quite understand this. Two software centers that are different ?

To avoid my confusion, can you take a screen shot of both and post them back here.

@Old_Gray_Wolf. Policy kit or bus error ? the config file posted looks fine though.

@OP can you post the output of this command back here

```
ps aux | grep [p]olkit-gnome-authentication-agent-1
```

Kind regards

---

### Post by Old_Grey_Wolf on 2012-03-30
> **matt_symes said:**
> 
@Old_Gray_Wolf. Policy kit or bus error ? the config file posted looks fine though.

If Policy Kit isn't running it can cause this problem. It is not sometime I have experience troubleshooting though.

I'm watching from the side to see how it is done.

---

### Post by jorritTyb on 2012-03-31
> **matt_symes said:**
> Hi



I don't quite understand this. Two software centers that are different ?

To avoid my confusion, can you take a screen shot of both and post them back here.

@Old_Gray_Wolf. Policy kit or bus error ? the config file posted looks fine though.

@OP can you post the output of this command back here

```
ps aux | grep [p]olkit-gnome-authentication-agent-1
```

Kind regards

Ok, first screenshot is of the non-working software center:

[IMG]http://i40.tinypic.com/jsinu0.jpg[/IMG]

Second screenshot is of the working software center:

[IMG]http://i43.tinypic.com/2yzmy5s.jpg[/IMG]

It may be that both are actually the same program but they look differently and also the second one works while the first one doesn't.

Greetings,

---

### Post by dino99 on 2012-03-31
Are you using non genuine packages/archives like ppa ?
Via synaptic you should purge then reinstall it, and remove .local from /home (it will be cleanly rebuilt on next boot.

---

### Post by jorritTyb on 2012-03-31
> **dino99 said:**
> Are you using non genuine packages/archives like ppa ?
Via synaptic you should purge then reinstall it, and remove .local from /home (it will be cleanly rebuilt on next boot.

I'm not sure what that even means? How do I check?

Greetings,

---

### Post by gordintoronto on 2012-03-31
To see what repositories are being used, two commands:
ls /etc/apt/sources.list.d
cat /etc/apt/sources.list

I think something will look "off" in one of those outputs.

---

### Post by jorritTyb on 2012-03-31
> **gordintoronto said:**
> To see what repositories are being used, two commands:
ls /etc/apt/sources.list.d
cat /etc/apt/sources.list

I think something will look "off" in one of those outputs.

Ok

Still weird that one version of the software center works well and the other doesn't. One would expect both versions to fail if there was a problem in the output below:

```

root@jorritPC:~# ls /etc/apt/sources.list.d
google-earth.list  wxformbuilder-release-oneiric.list  wxformbuilder-release-oneiric.list.save
root@jorritPC:~# 
root@jorritPC:~# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://be.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://be.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://be.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://be.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://be.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://be.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://be.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
root@jorritPC:~# 

```

Greetings,

---

### Post by gordintoronto on 2012-03-31
Here are a couple of semi-random things you could try: uncheck the source code repositories in Software Sources, and select the main repositories instead of the Belgian (I think -- be?) ones.

---

### Post by matt_symes on 2012-04-01
Hi

Can you post the output of this command.

```
ps aux | grep [p]olkit-gnome-authentication-agent-1
```

Also you have a mixture of Oneric and natty repositories in your sources.list file.

Remove the references to the natty repositories.

First make a backup of the existing file

```
sudo cp /etc/apt/sources.list{,.bk}
```

Then remove the lines from the existing file.

```
sudo sed -i '/natty/d' /etc/apt/sources.list
```

Kind regards

---

### Post by jorritTyb on 2012-04-02
> **matt_symes said:**
> Hi

Can you post the output of this command.

```
ps aux | grep [p]olkit-gnome-authentication-agent-1
```


Nothing. This command turns up nothing at all. I'm wondering if you didn't mean [pP] though instead of just [p]. In any case, that turns up nothing either.

> 
Also you have a mixture of Oneric and natty repositories in your sources.list file.

Remove the references to the natty repositories.

First make a backup of the existing file

```
sudo cp /etc/apt/sources.list{,.bk}
```

Then remove the lines from the existing file.

```
sudo sed -i '/natty/d' /etc/apt/sources.list
```

Kind regards

That didn't help. I just noticed something else. If I switch to the 'install packages' view in the ubuntu software center I get a semi non-graphical (very bland looking) tree view while it used to be much more fancy before. And the tree view isn't working either. I see the categories but I can't click on any. This is certainly a regression too. I just didn't notice this before because I don't go look that much there.

Anyway, the 'Install' button remains broken with above change.

Greetings,

---

### Post by matt_symes on 2012-04-02
Hi

You should be seeing something like this

```
matthew@matthew-Aspire-7540:~$ ps aux | grep [p]olkit-gnome-authentication-agent-1
matthew   2142  0.0  0.1 303652  3112 ?        Sl   10:19   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
matthew@matthew-Aspire-7540:~$ 

```

I believe you need polkit-gnome-authentication-agent-1 running to use authentication. This may be your problem. I think this is why it works if you use gksudo but not if you do not (I am not 100% sure on this but it's an avenue to explore).

We need to find out why it's not being started and that will need some research. 

In the meantime, please post the output of 

```
ls -l /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

That is a small L after ls.

The second set of commands i posted were never meant to fix your system. They are only supposed to clean up your sources.

Kind regards

---

### Post by jorritTyb on 2012-04-02
> **matt_symes said:**
> Hi
```
ls -l /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

That is a small L after ls.
Kind regards

Yes. I know how 'ls' works :-)

Anyway, here is the output:

```

root@jorritPC:~# ls -l /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
-rwxr-xr-x 1 root root 44648 2011-09-07 07:46 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

```

Greetings,

---

### Post by jorritTyb on 2012-04-02
I just now noticed that 'users-admin' when run from the menu also doesn't appear to be working correctly. The 'Add' button does nothing. Presumably because it also needs root.

However, gksudo users-admin doesn't help. Now the tool simply blocks right after startup.

It sounds like something that is supposed to give root access to graphical apps is seriously broken.

Greetings,

---

### Post by matt_symes on 2012-04-02
Hi

> **jorritTyb said:**
> I just now noticed that 'users-admin' when run from the menu also doesn't appear to be working correctly. The 'Add' button does nothing. Presumably because it also needs root.

However, gksudo users-admin doesn't help. Now the tool simply blocks right after startup.

It sounds like something that is supposed to give root access to graphical apps is seriously broken.

Greetings,

You have a problem with policy kit. 99% sure that's the issue especially after you checked the users button and that also did not work.

We need to find out why, however i am not going to be about until tomorrow evening. It's late here and tomorrow i have a busy day.

If nobody else jumps in then we can take this up again tomorrow evening.

As for the ls -l comment i made; don't take what i said personally. Different people on these forums have differing experience with the CLI. I have to assume that posters may not know CLI commands. You do, so that is fine.

**BUMP*** this thread so it will reappear in my subscribed threads sections. It will save me searching for it.

Kind regards

---


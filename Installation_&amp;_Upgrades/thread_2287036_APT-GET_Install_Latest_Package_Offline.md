---
title: "APT-GET Install Latest Package Offline"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by huy-tran2 on 2015-07-16
Hello All,

I'm new to ubuntu and i've been playing with it for the last week.  I've managed to setup several VM's all running ubuntu which is to test out a new SCADA package (Ignition SCADA).  There's a windows version but I figure this is a good opportunity to learn Ubuntu and Ignition at the same time.  Talk about big learning curve.

So my problem is that this system is not connected to the internet.  Due to corporate policies I absolutely cannot have these machines connected to the internet.  So to get my packages installed I setup a local repository...OK Done!  I can install packages no problem now if I download them to a USB stick and copy to the local repository.  How do I install the latest copy of a software?

For example...I run

sudo apt-get update
sudo apt-get install firefox

but this installs/looks for firefox v22.xx

I'd like to upgrade to v28.xx.  If I uninstall then reinstall firefox it just keeps installing v22 even though I downloaded v28 and its in the repository.

If I type

sudo apt-get install firefox=28.0

it gives me an error "E: version '28.0' for 'firefox' was not found.

Is there somewhere I'm supposed to edit a list of latest versions?  Again, remember I don't have access to the internet.  I can't find a solution for this exact problem.  I can find solutions if machine is connected to the internet.

---

### Post by v3.xx on 2015-07-16
Verify it is available on your system.
```
apt-cache policy firefox
```
And what version of ubuntu are you running (12.04; 14.04; 15.04)?

---

### Post by huy-tran2 on 2015-07-16
I'm running 14.04.

Sorry I made a mistake I meant I currently have version 28 and want to upgrade to version 39

I ran

apt-cache policy firefox and it came back with

```
firefox:
 Installed: 28.0+build2-0ubuntu2
 Candidate: 28.0+build2-0ubuntu2
 Version Table:
*** 28.0+build2-0ubuntu2 0
                    500 file:/home/scadadeveloper/repository/trusty/main amd64 Packages
                    100 /var/lib/dpkg/status
```

I went to the /var/lib/dpkg/status directory and see two files.  One is called "available" and the other is called "status".  Is the "status" one a list of what is installed?  Do I edit the one called "available"?

---

### Post by ian-weisser on 2015-07-16
```
$ rmadison firefox | grep trusty
 firefox | 28.0+build2-0ubuntu2           | trusty                   | source, amd64, armhf, i386, powerpc
 firefox | 31.0+build1-0ubuntu0.14.04.1   | trusty-security          | arm64
 firefox | 31.0+build1-0ubuntu0.14.04.1   | trusty-updates           | arm64
 firefox | 39.0+build5-0ubuntu0.14.04.1   | trusty-security          | source, amd64, armhf, i386, powerpc, ppc64el
 firefox | 39.0+build5-0ubuntu0.14.04.1   | trusty-updates           | source, amd64, armhf, i386, powerpc, ppc64el
```

You seem to not have the trusty-updates repository enabled. This will automatically update Firefox to 39.
You also seem to not have the trusty-security repositories enabled (very bad).
Both are trivial to fix in your System Settings --> Software & Updates control panel --> updates tab.

EDIT: Oh...offline. See the apt-zip package or Synaptic application for two easier ways to update software offline. 
It's very easy to download the latest firefox package from Launchpad.net onto a USB stick and sneakernet it to your system.
The hard part is to know what dependencies of the latest firefox package also need to be updated for it to work. That's what apt-zip and Synaptic (and others) do.

---

### Post by huy-tran2 on 2015-07-17
Its enabled.  Like i mentioned above...I have no internet.

---

### Post by v3.xx on 2015-07-17
I guest you have reasons for updating a browser without internet.

As pointed out, the update will be automatic once connected to the internet.

A manual edit of dpkg is not recommended.  there are other ways to update offline.  I do not myself, but can point you here.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=offline+update&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=offline+update&sa=Search&cof=FORID:9)

---


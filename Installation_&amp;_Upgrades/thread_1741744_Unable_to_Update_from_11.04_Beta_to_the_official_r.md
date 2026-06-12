---
title: "Unable to Update from 11.04 Beta to the official release"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by LiciLee on 2011-04-28
When I run sudo apt-get update -d it starts the update process
I get this: 

Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en
  Unable to connect to extras.ubuntu.com:http:
Fetched 4,928 B in 21s (234 B/s)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en)  Unable to connect to extras.ubuntu.com:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.


This has happened every time and it also happens when I just do sudo apt-get update. What can I do to update so that I don't loose everything that I've been working on? :confused:

On a side note, I can't open software center either, when I select the categories, it just starts to load and keeps loading without giving me anything.

---

### Post by tribalboy on 2011-04-28
I tried  ```
update-manager -d
``` to load the update manager and go from there & it seems to have done it

---

### Post by mörgæs on 2011-04-28
It could be because the servers are overloaded now.

---

### Post by LiciLee on 2011-04-28
No because I haven't been able to update for the last week at least. 

when I run update-manager -d I get this:

[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'[/B]

---

### Post by madjr on 2011-04-28
i would suggest people downloading the iso to use torrents, to help the servers a bit.

also if you burn the iso, it now has the option to upgrade from it

---

### Post by LiciLee on 2011-04-28
I was trying to do that and am currently downloading the iso, I was just looking for other options since the iso is such a large file.

---

### Post by Blasphemist on 2011-04-28
I believe that is telling you that you have a broken package. I'd try using synaptic, edit menu, fix broken packages. If that still didn't fix the issue, I'd back up home and try using the cd to do the upgrade.

There is an upgrade option on the iso as previously posted. You could do a clean install and then copy back the backed up home you made but that might be a bit drastic right now.

---

### Post by LiciLee on 2011-04-28
I tried to do the package manager method and I got the following error: 
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by Blasphemist on 2011-04-28
In package manager, when did you get the error? Was it at the end after you'd applied marked changes to fix broken packages? Did you get the summarized changes that would be applied?

You could try using ```
apt-cache unmet
```

This will display a summary or all unmet dependencies in the package cache. If for some reason even this can't open the cache that would also tell us something. 

This may be more to the point. Use this code to display some statistics about the cache. ```
apt-cache stats
```

Use ```
man apt-cache
``` if you have any questions on this command.

---

### Post by tgm4883 on 2011-04-28
> **LiciLee said:**
> When I run sudo apt-get update -d it starts the update process
I get this: 

Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en
  Unable to connect to extras.ubuntu.com:http:
Fetched 4,928 B in 21s (234 B/s)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en)  Unable to connect to extras.ubuntu.com:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.


This has happened every time and it also happens when I just do sudo apt-get update. What can I do to update so that I don't loose everything that I've been working on? :confused:

On a side note, I can't open software center either, when I select the categories, it just starts to load and keeps loading without giving me anything.

If you are already on natty beta why are you using "apt-get update -d"?

Just use apt-get update then apt-get upgrade

---

### Post by kansasnoob on 2011-04-28
Would someone please show me where they came up with the idea of running "sudo apt-get update -d".

Please show the documentation that you followed to do that :D

If you're running the Beta of a new release it should just update to the final with very rare exception, unless you've somehow hosed your software sources :)

But the servers are totally flooded today, even the zsync server!

---

### Post by Blasphemist on 2011-04-28
> **kansasnoob said:**
> Would someone please show me where they came up with the idea of running "sudo apt-get update -d".

Please show the documentation that you followed to do that :D

If you're running the Beta of a new release it should just update to the final with very rare exception, unless you've somehow hosed your software sources :)

But the servers are totally flooded today, even the zsync server!

Somehow the OP had that idea. Other than that, some of us just didn't recognize that OP was already on natty. Our error.

So does the OP need to do anything now to get things back to a state where a normal update will complete without error? I just want to know for learning purposes.

---

### Post by LiciLee on 2011-04-28
In other forms on here about updating, that's what it said. I'm used to doing distro updates but this is my first time updating from a beta. I tried using the CD method and that's not working either. I'm getting the same problem just trying to install 11.04. I'm going to try to do a fresh install of 10.10 and then update from there to 11.04 and see if that works. In the meantime while I wait for the 10.10 to download, does anyone have any suggestions as to what I might be able to do?

---

### Post by Blasphemist on 2011-04-28
I'd try to hold up on going back and then forward. I'm guessing that flags or some such thing needs reset but let's see if others more knowledgeable than I answer back.

---

### Post by Interista on 2011-04-28
> **tgm4883 said:**
> If you are already on natty beta why are you using "apt-get update -d"?

Just use apt-get update then apt-get upgrade
[COLOR=Navy]I did what u said but i got this :
"W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
"

same problem in Update Manger :
[http://ubuntuforums.org/showthread.php?t=1741841](http://ubuntuforums.org/showthread.php?t=1741841)[/COLOR]

---

### Post by Blasphemist on 2011-04-28
> **Interista said:**
> [COLOR=Navy]I did what u said but i got this :
"W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
"

same problem in Update Manger :
[http://ubuntuforums.org/showthread.php?t=1741841](http://ubuntuforums.org/showthread.php?t=1741841)[/COLOR]

That looks to me like the servers were just too busy and you didn't connect. Try just waiting if possible as the servers are extremely busy today.

---

### Post by kansasnoob on 2011-04-28
It's hard to find a place to start :(

---

### Post by Blasphemist on 2011-04-28
> **kansasnoob said:**
> It's hard to find a place to start :(

I know you're likely real busy today kansasnoob but if you can point us in a direction I'll help OP figure it out if needed. In the meantime I'll try to figure it out.

---

### Post by Interista on 2011-04-28
> **Blasphemist said:**
> That looks to me like the servers were just too busy and you didn't connect. Try just waiting if possible as the servers are extremely busy today.
[COLOR=Navy] Ok thnx for help , I think i will just wait ^^"[/COLOR]

---

### Post by tgm4883 on 2011-04-28
> **Interista said:**
> [COLOR=Navy]I did what u said but i got this :
"W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
"

same problem in Update Manger :
[http://ubuntuforums.org/showthread.php?t=1741841](http://ubuntuforums.org/showthread.php?t=1741841)[/COLOR]

That never worked. The sun-java-community-team doesn't have any natty builds [https://launchpad.net/~sun-java-community-team/+archive/sun-java6/+packages](https://launchpad.net/~sun-java-community-team/+archive/sun-java6/+packages)

---

### Post by Interista on 2011-04-28
> **tgm4883 said:**
> That never worked. The sun-java-community-team doesn't have any natty builds [https://launchpad.net/~sun-java-community-team/+archive/sun-java6/+packages]("https://launchpad.net/%7Esun-java-community-team/+archive/sun-java6/+packages")
Ok but i should to do now :S ?

---

### Post by tgm4883 on 2011-04-28
> **Interista said:**
> Ok but i should to do now :S ?

You need to remove the line pointing to that PPA from /etc/apt/sources.list or find the .list file that corresponds to that ppa in /etc/apt/sources.list.d/

---

### Post by Interista on 2011-04-28
[COLOR=Navy]I just went to Settings in Update Manger then to other software tab ..
unchecked the couple of APT (sun java6) & it's works now ..
but now it keeps saying "Your system up-to-date" :(
[/COLOR]

---

### Post by Blasphemist on 2011-04-28
> **tgm4883 said:**
> You need to remove the line pointing to that PPA from /etc/apt/sources.list or find the .list file that corresponds to that ppa in /etc/apt/sources.list.d/

Do you know how to solve the issue for the OP? I don't. See kansasnoob last post in this thread please.

---

### Post by tgm4883 on 2011-04-28
> **Blasphemist said:**
> Do you know how to solve the issue for the OP? I don't. See kansasnoob last post in this thread please.

I looked at kansasnoob last few posts but I couldn't see the issue. My initial response to the OP was "Just use apt-get update then apt-get upgrade". To answer kansasnoob's last question regarding the -d option, with apt-get the -d option means download only. It has absolutely no effect on an 'apt-get update'. If you run it with 'apt-get upgrade' it will download the updates but not install them.

None of that appears to be the OP's issue though. It just appears that the repos are overloaded. Looking at the repos, they do exist for natty.

---

### Post by Interista on 2011-04-29
[COLOR=navy]Any solutions ? :([/COLOR]

---

### Post by Blasphemist on 2011-04-29
> **tgm4883 said:**
> I looked at kansasnoob last few posts but I couldn't see the issue. My initial response to the OP was "Just use apt-get update then apt-get upgrade". To answer kansasnoob's last question regarding the -d option, with apt-get the -d option means download only. It has absolutely no effect on an 'apt-get update'. If you run it with 'apt-get upgrade' it will download the updates but not install them.

None of that appears to be the OP's issue though. It just appears that the repos are overloaded. Looking at the repos, they do exist for natty.

He's saying that it should work using this code I believe. Unless the servers are still overloaded.

```
apt-get update
apt-get upgrade
```

---

### Post by Interista on 2011-04-29
> **Blasphemist said:**
> He's saying that it should work using this code I believe. Unless the servers are still overloaded.
 
```
apt-get update
apt-get upgrade
```
[COLOR=navy]BTW i used these command too, but terminal keep saying " 0 new updates etc. " :([/COLOR]

---

### Post by Blasphemist on 2011-04-29
> **Interista said:**
> [COLOR=navy]BTW i used these command too, but terminal keep saying " 0 new updates etc. " :([/COLOR]

Are you sure you're not current then?

---

### Post by Interista on 2011-04-29
> **Blasphemist said:**
> Are you sure you're not current then?
[COLOR=navy]I already updated to 11.04 BETA before couple of days ..
 but i don't to official version ..[/COLOR]
[COLOR=navy]i just installed normal updates not the release .. [/COLOR]
[COLOR=navy]btw how i can know what's version i have ?[/COLOR]

---

### Post by Blasphemist on 2011-04-29
I don't remember the command to display it but the automatic updates do take you to the release from the beta so I'm sure you are current at the release.

---

### Post by Interista on 2011-04-29
> **Blasphemist said:**
> I don't remember the command to display it but the automatic updates do take you to the release from the beta so I'm sure you are current at the release.
[COLOR=navy]U mean Updates manger don't notice me if there Official release like when i updated to BETA ,, just update to the final release !?![/COLOR]
[COLOR=navy]if u get the command tell me and thank u so much for help ^_^[/COLOR]

---

### Post by Blasphemist on 2011-04-29
What I mean is that update manager takes you from beta to the release automatically.

---


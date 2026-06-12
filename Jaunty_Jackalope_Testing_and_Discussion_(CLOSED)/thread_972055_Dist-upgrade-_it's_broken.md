---
title: "Dist-upgrade- it's broken ?"
date: 2008-11-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-11-05
Just tried 
```
sudo aptitude dist-upgrade
```
and found some broken packages (expected ?)
```
$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
The following packages are BROKEN:
  docbook-xml libcompress-zlib-perl update-manager 
The following packages will be upgraded:
  libcompress-raw-zlib-perl libio-compress-base-perl 
  libio-compress-zlib-perl update-manager-core 
5 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 832kB of archives. After unpacking 8192B will be used.
The following packages have unmet dependencies:
  docbook-xml: PreDepends: xml-core (>= 0.12) but 0.11ubuntu1 is installed.
  update-manager: Depends: update-manager-core (= 1:0.93.32) but 1:0.95 is to be installed.
  libcompress-zlib-perl: Depends: libio-compress-base-perl (< 2.011.~) but 2.015-1 is to be installed.
                         Depends: libio-compress-zlib-perl (< 2.011.~) but 2.015-1 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
libcompress-zlib-perl

Keep the following packages at their current version:
docbook-xml [4.5-5 (now)]
update-manager-core [1:0.93.32 (now)]

Leave the following dependencies unresolved:
libwww-perl recommends libcompress-zlib-perl
Score is 55

Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  libcompress-zlib-perl{a} 
The following packages will be upgraded:
  libcompress-raw-zlib-perl libio-compress-base-perl 
  libio-compress-zlib-perl 
3 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 259kB of archives. After unpacking 160kB will be freed.
Do you want to continue? [Y/n/?] y     
Writing extended state information... Done
Get:1 http://archive.ubuntu.com jaunty/main libio-compress-zlib-perl 2.015-1 [142kB]
Get:2 http://archive.ubuntu.com jaunty/main libio-compress-base-perl 2.015-1 [59.1kB]
Get:3 http://archive.ubuntu.com jaunty/main libcompress-raw-zlib-perl 2.015-1 [58.3kB]
Fetched 259kB in 1s (206kB/s)                
(Reading database ... 100567 files and directories currently installed.)
Removing libcompress-zlib-perl ...
Processing triggers for man-db ...
(Reading database ... 100551 files and directories currently installed.)
Preparing to replace libio-compress-zlib-perl 2.011-1 (using .../libio-compress-zlib-perl_2.015-1_all.deb) ...
Unpacking replacement libio-compress-zlib-perl ...
Preparing to replace libio-compress-base-perl 2.011-1 (using .../libio-compress-base-perl_2.015-1_all.deb) ...
Unpacking replacement libio-compress-base-perl ...
Preparing to replace libcompress-raw-zlib-perl 2.011-2build1 (using .../libcompress-raw-zlib-perl_2.015-1_amd64.deb) ...
Unpacking replacement libcompress-raw-zlib-perl ...
Processing triggers for man-db ...
Setting up libcompress-raw-zlib-perl (2.015-1) ...
Setting up libio-compress-base-perl (2.015-1) ...
Setting up libio-compress-zlib-perl (2.015-1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

Current status: 2 updates [-3].
```

---

### Post by plun on 2008-11-05
You are using the most powerful command for upgrades, also for **total brakes**.

I am only using aptitude if I am sure about what aptitude proposes or just to take a look if a package is broken or kept back.
[B]
docbook-xml is kept-back with apt[/B]

xml-core is broken

```
plun@plun:~/$ sudo apt-get install docbook-xml
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  [B]docbook-xml: PreDepends: xml-core (>= 0.12) but 0.11ubuntu1 is to be installed
E: Broken packages[/B]

```


I have no hurry....  it takes some time to check all consequenses.

---

### Post by cariboo on 2008-11-05
At this point in the development of Jaunty, I always use:

```
sudo aptitude safe-upgrade
```

That way nothing important gets uninstalled. As it stands right now I have 5 packages that are uninstallable, I can wait till the rest of the depencies are available to install the  5 packages.

Jim

---

### Post by ghandi69_ on 2008-11-05
I was hoping this would apply to my issue.. but anyway.. I'm using 8.04.  And I get the following....

```

tony@Ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Why will it not let me upgrade to 8.10?

---

### Post by plun on 2008-11-05
> **ghandi69_ said:**
> 
Why will it not let me upgrade to 8.10?

Please use the recommended way

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Also to read known issues can maybe be important.

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Good Luck !

---

### Post by Kevbert on 2008-11-05
> **ghandi69_ said:**
> I was hoping this would apply to my issue.. but anyway.. I'm using 8.04.  And I get the following....

```

tony@Ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Why will it not let me upgrade to 8.10?

Regarding your distribution upgrade. If you want to upgrade to 8.10 you need to select System-Administration-Software Sources-Updates tab and select 'Normal Releases' under the Release Upgrade Heading.  From there you can use sudo apt-get dist-upgrade from terminal or use Update Manager and tick the box for Ubuntu 8.10.

---

### Post by xebian on 2008-11-05
> **Kevbert said:**
> Just tried 
```
sudo aptitude dist-upgrade
```
and found some broken packages (expected ?)
```
$ sudo aptitude dist-upgrade
Reading package lists... Done

..
Current status: 2 updates [-3].
```

'dist-upgrade' is not a valid action for aptitude.  ):P

---

### Post by Kevbert on 2008-11-05
> **xebian said:**
> 'dist-upgrade' is not a valid action for aptitude.  ):P

Oops, should have used apt-get. According to the 'man' page it isn't, but it doesn't give an error for the command, only the action.

---

### Post by danf_1979 on 2008-11-05
Personally, I'm a little afraid of upgrading some core libraries at this time. Till now, I'm only updating by hand what I consider to be "safe" packages (like phpmyadmin, or nothing too risky). Anyone also doing this?

I think I'll wait a little, maybe till alpha1 to upgrade the core libraries. Anyone has any thoughts on this?

---

### Post by xebian on 2008-11-05
> **Kevbert said:**
> Oops, should have used apt-get. According to the 'man' page it isn't, but it doesn't give an error for the command, only the action.

The only plausible explanation - 'aptitude' is an alias for 'apt-get' in your system.  Not a big deal, but I pointed that out only so that unsuspecting users are not confused.  :smile:

---

### Post by plun on 2008-11-05
well...   dist-upgrade is a valid command.

> This command was originally named dist-upgrade for historical reasons, **and aptitude still recognizes dist-upgrade as a synonym for full-upgrade**. 

[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/rn01re01.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/rn01re01.html)

The key issue here is that Aptitude is more powerful then Apt.

Aptitude gives proposals for a solution, also gives a "hint" about how good it can be.

I have totally broke a handful of installs with Aptitude solutions, so be careful....):P

---

### Post by xebian on 2008-11-05
> **plun said:**
> well...   dist-upgrade is a valid command.



[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/rn01re01.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/rn01re01.html)

..

Thanks for the historical lesson.  :)

IMHO it should emit a message when used that it's been deprecated.  Unsuspecting users may not want the full-upgrade.  What other behaviors that are not apparent?  No wonder a lot of people are not happy with aptitude.   :(

---

### Post by ShirishAg75 on 2008-11-05
There is a thread ongoing on for future revisions and stuff people want on aptitude-devel, 

[http://lists.alioth.debian.org/mailman/listinfo/aptitude-devel](http://lists.alioth.debian.org/mailman/listinfo/aptitude-devel)

Look for the thread Plans for aptitude 0.5.0 - 0.6.0

If you have suggestions or something, that would be the right place to put there. Remember to subscribe to the mailing list first :)

---

### Post by plun on 2008-11-06
> **xebian said:**
> Thanks for the historical lesson.  :)

IMHO it should emit a message when used that it's been deprecated.  Unsuspecting users may not want the full-upgrade.  What other behaviors that are not apparent?  No wonder a lot of people are not happy with aptitude.   :(

Well... aptitude is powerful but the challenge is a user which is tempded to follow a advice without an emergency plan.

During a "**Debian import**", as it is now, it can be several deep nested breakages nearly impossible to fix  

Debian Sids inofficial FAQ can be used in this situation...
[http://wooledge.org/~greg/sidfaq.html](http://wooledge.org/~greg/sidfaq.html)

---

### Post by Gina on 2008-11-06
Seems to me that unless you're a developer and/or really experienced in Linux it is better to wait a week or two while everything is put together.  It's my guess that alpha 1 is the point at which the developers would like the main testers to start testing for bugs.  It gives me the message "Here you are folks, see what you think of this - give it a good going over".

---


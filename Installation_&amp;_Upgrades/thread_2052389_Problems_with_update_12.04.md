---
title: "Problems with update 12.04"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by miskosu on 2012-09-03
Hello all

As always the best place to search for answers :)

To cut to the chase:
I have a problem with the updates...

For 2-3 weeks now, I cannot update my precise pangolin, neither with command line, update manager and even cannot open the synaptic manager.

The errors are with some headers of the packages.

In the Update manager, when I open it:
> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/packages.debian.org_librxtx-java_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
In Synaptic :
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/packages.debian.org_librxtx-java_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.And in command line:
> W: GPG error: [http://packages.debian.org](http://packages.debian.org) precise InRelease: File /var/lib/apt/lists/partial/packages.debian.org_librxtx-java_dists_precise_InRelease doesn't start with a clearsigned message
W: Failed to fetch [http://packages.debian.org/librxtx-java/dists/precise/main/i18n/Index](http://packages.debian.org/librxtx-java/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/packages.debian.org_librxtx-java_dists_precise_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.
I searched the forum and found that for many ppl, these 4 commands fixed the problem:
> rm /var/lib/apt/lists/* -vf
apt-get clean
apt-get update
apt-get upgradeBut there was no success for me there...

I tried to change servers from which to download but no luck either...

And that`s when I turned here for help

I`m running a Lenovo G550 with Ubuntu 12.04 32bit if you need that information.

I would be very grateful if someone could help me out.

Forward thank you

Forgot to tell you that the problems are with the source list:
[http://packages.debian.org/librxtx-java](http://packages.debian.org/librxtx-java) precise main
I figure that it is a essential update, but it does not work....

---

### Post by grahammechanical on 2012-09-03
I may be able to help you. I had a similar problem on my 12.10 installation. It should not happen on a Ubuntu distribution release like 12.04 but I also had this problem on my 12.04 install the other day.

There are two commands to run.

```
sudo rm /var/lib/apt/lists/* -rf
```

That removes/deletes all the files/scripts in the lists folder/directory.

```
sudo apt-get update
```

will bring in new scripts that should not be broken.

Regards.

P.S. Looking at your post again I see that the problem file/script is in the /var/lib/apt/lists/partial folder/directory. That is why the remove command failed to solve the problem. You only removed and replaced the files in the lists folder not in the partial folder within the lists folder. If you get what I am saying.

So the command should be

```
sudo rm /var/lib/apt/lists/partial/* -rf
```

The partial folder on my system is empty. But on your system it, evidently has something in it that is blocking Update Manager from doing it stuff

---

### Post by miskosu on 2012-09-04
> **grahammechanical said:**
> I may be able to help you. I had a similar problem on my 12.10 installation. It should not happen on a Ubuntu distribution release like 12.04 but I also had this problem on my 12.04 install the other day.

There are two commands to run.

```
sudo rm /var/lib/apt/lists/* -rf
```That removes/deletes all the files/scripts in the lists folder/directory.

```
sudo apt-get update
```will bring in new scripts that should not be broken.

Regards.

P.S. Looking at your post again I see that the problem file/script is in the /var/lib/apt/lists/partial folder/directory. That is why the remove command failed to solve the problem. You only removed and replaced the files in the lists folder not in the partial folder within the lists folder. If you get what I am saying.

So the command should be

```
sudo rm /var/lib/apt/lists/partial/* -rf
```The partial folder on my system is empty. But on your system it, evidently has something in it that is blocking Update Manager from doing it stuff

Hello,

Thank you for your reply.

I tried that already but with no luck, deleted the contents of lists folder, and the partial folder too, but nothing. Still gives me the error. :(

So any other ideas are very welcome.

---


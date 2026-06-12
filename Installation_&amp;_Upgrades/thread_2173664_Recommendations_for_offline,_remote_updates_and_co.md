---
title: "Recommendations for offline, remote updates and config management?"
date: 2013-09-10
forum: Installation &amp; Upgrades
---

### Post by UsernameNumber on 2013-09-10
Hello all, 

I'm working with a Kenya-based non-profit (tunapanda.org) that uses OSS to provide computing resources to schools where bandwidth is either nonexistent or prohibitively expensive. We provide a customized Edubuntu/LTSP setup which will host local versions of useful online resources like Kahn Academy (via ka-lite), Wikipedia (via Wikipedia For Schools), etc. 

I'm serving as a sort of tech/Linux advisor for them, but not only have I never maintained a system with these particular challenges (details below), my knowledge is a bit out of date, and most of my experience is on the Red Hat side of things, so I'm still getting used to and learning about a lot of the Debian-isms over here. 

My question is, how would you manage updates and configuration changes on a server that:
[LIST=1]
[*]Is not physically accessible to you.
[*]Has user data (so you can't just reinstall the whole system)
[*]Does not have net access (local reps can download software to a USB drive and then bring it to the school).
[*]Does not have much in the way of local technical expertise (so deployment would need to be pretty simple).
[/LIST]

So far, the idea that seems most feasible is to do one of the following: 

If all the user and server-specific data can be kept on its own partition(s) then maybe we could just do a full re-install for every update, using a preseed that re-uses, say, /home and /usr/local without formatting them. This is pretty easy with Kickstart, but I haven't tried it with a preseed file yet. 

- or -

Set up the initial deployment to use a local apt repository containing packages that deploy our customizations, then deploy updates by...
[LIST=1]
[*]Creating/updating packages that make any needed changes, and storing them in a remote repo
[*]Local person downloads the repository data to a USB drive
[*]Repo data is rsync'd from the USB drive to the local dir on the server
[*]apt-get update && apt-get upgrade
[/LIST]

Not having worked with .deb files much, I'm a bit concerned about conflicts. What if, say, we need to make changes to a monolithic config file (on without a convenient conf.d directory)? Is there a trick to avoid complications when the file is owned (and likely to be updated) by another package? 

Anyway, before I devote too much time and effort to researching these options, I wanted to see if anyone else has ideas for what to try, just in case there's a magic bullet out there that I haven't heard about (has anyone used Chef or similar in a situation like this?).

Thanks!

---

### Post by ian-weisser on 2013-09-11
> **UsernameNumber said:**
> how would you manage updates and configuration changes on a server that:
[LIST=1]
[*]Is not physically accessible to you. 
[*]Has user data (so you can't just reinstall the whole system) 
[*]Does not have net access (local reps can download software to a USB drive and then bring it to the school). 
[*]Does not have much in the way of local technical expertise (so deployment would need to be pretty simple). 
[/LIST]


1) The novice rep/admin on-site needs to be trained (30-60  minutes) how to document configuration changes properly, and how to use  documentation to understand (and revert) past config changes.

2)  Backups. Regular backups. "Can't reinstall" seems like a recipe for  project failure. What if some poor fool fumble-fingers a command and  re-permissions a whole tree? Or what will you do in two years when they  want some new application that's only available in a later verion of  Ubuntu? I think reinstallation from scratch, and restoration of data  from backups are essential tasks. Not common, nor frequent, nor  difficult, but essential.

3) The apt-zip and apt-offline packages both make handling offline updates easy and convenient. 

4)  Seems like an organizational or training issue to me. For example, one  way to handle it is for the local reps to feed feature/config/package requests to the  parent organization, then for the parent org to train the local rep how  to properly implement and maintain the feature/config/package.

---

### Post by UsernameNumber on 2013-09-11
I hear you on the backups. We have very limited resources, but I'm already looking into whether we can provide at least a USB drive for each classroom toward this end. Any recommendations for a backup system? I've always just used rsync, but it's probably not the best, and definitely not the most user-friendly option.

Re using apt-zip and apt-offline, see my question earlier about conflicts between packages. Wouldn't that be a problem? I'm also looking into whether this could be done with a set of Puppet manifests instead, but if there's an easy way to deploy config changes, including changes to files provided by other packages, that would be welcome news.

---

### Post by ian-weisser on 2013-09-11
> **UsernameNumber said:**
> Any recommendations for a backup system? I've always just used rsync

I like rsync.
An external USB drive, and the knowledge of how to use it, is all you really need.

Perhaps a simple script: Udev can recognize UUIDs and trigger root-level scripts. Look in /etc/udev/rules.d/  Mount, rsync, unmount. Just plug in the drive with the correct UUID, and the rest is automagic.


> **UsernameNumber said:**
> Re using apt-zip and apt-offline, see my question earlier about  conflicts between packages. Wouldn't that be a problem?

Should not be a problem. Apt still figures out all dependencies for you, including protection from conflicts and wrong versions.

---

### Post by UsernameNumber on 2013-09-11
First, thanks very much for the replies!

Second, could you elaborate on this a bit?

> **ian-weisser said:**
> Should not be a problem. Apt still figures out all dependencies for you, including protection from conflicts and wrong versions.

For example, suppose */etc/foo.conf* is provided by the ***foo*** package, and I want to make customizations to it. The way I'm imagining this, I would create a ***tunapanda-foo-config*** package that depends on ***foo*** being installed and overwrites */etc/foo.conf*. I haven't seen any docs that explain how I tell apt that my package should be allowed to overwrite *foo.conf* (I'm assuming it wouldn't normally be allowed to), nor how to prevent updates to the ***foo*** package from overwriting my version of *foo.conf*.

Links to the relevant docs are welcome, I just haven't been able to find any so far.

---

### Post by ian-weisser on 2013-09-11
Apt generally won't care if you are overwriting foo.conf. Apt only cares that foo was indeed installed. What you do after installation is complete is not Apt's care.

One way to accomplish foo with a custom config is to use a simple script.
Another way is to use a dummy package that handles the dependencies and overwrites foo.config during the install-script segment.
Another, more elegant way is to edit the package itself to include your preferred conf file instead of the default, and then to distribute your customized package.

Many packages put non-default config changes somewhere else (like /etc/foo/config.d/ or /home/$USER/.config/foo )
Many system-level config files can be changed using the installer preseed file.

You can also, of course, use good old patch files to replace anything you wish, including config files.

You are quite right that updating a package with a custom config may overwrite the customization. Or it may not. Or it may ask the admin to choose old/new/merge. That's why many packages keep customizations separate. You can also avoid upgrading those packages using apt-pinning or manually.

Er, did that answer the question?

---

### Post by UsernameNumber on 2013-09-11
I think it did! Thanks!

---


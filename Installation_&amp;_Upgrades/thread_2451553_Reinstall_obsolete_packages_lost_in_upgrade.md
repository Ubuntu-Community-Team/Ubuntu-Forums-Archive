---
title: "Reinstall obsolete packages lost in upgrade"
date: 2020-10-06
forum: Installation &amp; Upgrades
---

### Post by afollette on 2020-10-06
Hi All,

I recently upgraded to from Ubuntu 20.04 from 18.04. I unintentionally removed the obsolete packages during the process. However, I have several packages that are essential to my day to day activities. However, they are not found in any of my apt repositories.
I found one I needed on debian.pkgs.org [https://debian.pkgs.org/9/debian-main-amd64/libwebkitgtk-1.0-0_2.4.11-3_amd64.deb.html](https://debian.pkgs.org/9/debian-main-amd64/libwebkitgtk-1.0-0_2.4.11-3_amd64.deb.html) However, when I install this package the dependencies are also not in any of my apt repositories:

```

sudo apt install libwebkitgtk-1.0-0:amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libwebkitgtk-1.0-0 is already the newest version (2.4.11-3).
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 libwebkitgtk-1.0-0 : Depends: libjavascriptcoregtk-1.0-0 (= 2.4.11-3) but it is not installable
                      Depends: libicu57 (>= 57.1-1~) but it is not installable
                      Depends: libjpeg62-turbo (>= 1.3.1) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

``` 

 I assumed these were in the bionic beaver repositories. Is there a way I can search those repositories and see? Can anyone recommend a solution?

Cheers!

---

### Post by TheFu on 2020-10-07
Situations like this is why Linux Containers are great.  Create an LXD 18.04 container and load the apps you still need into it. You'll need to patch it weekly, just like the 20.04 OS, but there really shouldn't be much overhead in running the program(s) inside the container.  There will probably be some difficulties if the programs are GUI tools, however.  I'm not 100% certain how to accomplish that, but there have been a few posts here for setting up an LXD to run GUI programs.

The "container" will be much smaller that a full OS and running programs inside it are basically like snaps, but you get to control it, unlike with ... er ... snap packages.

Anyways, just an option for consideration.  I may need to do the same for a few GUI programs in the next 6 months. Just haven't gotten there yet.

---

### Post by Tadaen_Sylvermane on 2020-10-07
I have done with gui over an ssh tunnel. Not the best for everything, but just text editors like Kate it works fine.

You voulf also add the bionic source lines to your system. Build against 20.04 and see what happens. Ive done this in the past as well.

---

### Post by afollette on 2020-10-08
> Create an LXD 18.04 container and load the apps you still need into it.  You'll need to patch it weekly, just like the 20.04 OS, but there  really shouldn't be much overhear in running the program(s) inside the  container.  There will probably be some difficulties if the programs are  GUI tools, however.  I'm not 100% certain how to accomplish that, but  there have been posts here for setting up an LXD to run GUI programs.

The problem here is that the software is for my VPN. Would I be able to run my VPN within a container and still forward all of my traffic through it? It seems like it is possible, but I can't gauge how difficult a solution it will be. Also, with GUI apps you can X11 forward to run them.

> You voulf also add the bionic source lines to your system. Build against  20.04 and see what happens. Ive done this in the past as well.

I am trying this now. I've added all the bionic repositories to my source.list and I'm trying to install the package. Let's see how it goes!

Thanks for the ideas guys.

---

### Post by CelticWarrior on 2020-10-08
If you really have such specific needs and considering Ubuntu 18.04 is supported until April 2023 then the release upgrade was a bad idea.

Do not to retrofit old software in a current release. If such software is no longer available there's a reason for that.

Yes, it's certainly possible to run it in a container or VM, many users have it that way, but using a still supported release where you know the software works is a much better idea. Anything you can do now other than getting back to 18.04 is complicated to another level and takes a lot more time and effort than just reinstalling the previous LTS release.

---

### Post by deadflowr on 2020-10-08
It's not this
[https://askubuntu.com/questions/1135065/cant-run-pulse-secure-on-ubuntu-19-04-because-libwebkitgtk-1-0-so-0-is-missing]("https://askubuntu.com/questions/1135065/cant-run-pulse-secure-on-ubuntu-19-04-because-libwebkitgtk-1-0-so-0-is-missing")
is it?

For what it's worth, part of you issue is the fact you grabbed the Debian version of the package,
Debian and Ubuntu, while much alike, do have differences.
Ubuntu's libwebkitgtk1.0-0 package requires different dependencies than the Debian package does.

---

### Post by afollette on 2020-10-12
> **deadflowr said:**
> It's not this
[https://askubuntu.com/questions/1135065/cant-run-pulse-secure-on-ubuntu-19-04-because-libwebkitgtk-1-0-so-0-is-missing](https://askubuntu.com/questions/1135065/cant-run-pulse-secure-on-ubuntu-19-04-because-libwebkitgtk-1-0-so-0-is-missing)
is it?

For what it's worth, part of you issue is the fact you grabbed the Debian version of the package,
Debian and Ubuntu, while much alike, do have differences.
Ubuntu's libwebkitgtk1.0-0 package requires different dependencies than the Debian package does.

Yes, it is that. Thank you for posting the link.

I grabbed the 18.04 Ubuntu repositories and pulled the obsolete packages from there. However, I will look into this method. Thanks for the information.

>  If you really have such specific needs and considering Ubuntu 18.04 is  supported until April 2023 then the release upgrade was a bad idea.

Do not to retrofit old software in a current release. If such software is no longer available there's a reason for that.

Yes, it's certainly possible to run it in a container or VM, many users  have it that way, but using a still supported release where you know the  software works is a much better idea. Anything you can do now other  than getting back to 18.04 is complicated to another level and takes a  lot more time and effort than just reinstalling the previous LTS  release.

Yes, I understand this was a rookie mistake. I was not aware that these packages were becoming obsolete and that they would not run on 20.04. I will consider downgrading. Thanks for the help.

---


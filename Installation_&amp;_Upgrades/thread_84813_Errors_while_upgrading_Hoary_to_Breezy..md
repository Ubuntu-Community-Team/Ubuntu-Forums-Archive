---
title: "Errors while upgrading Hoary to Breezy."
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by duffmckagan on 2005-11-01
I have Kubuntu 5.04 Hoary Hedgehog installed on my computer.

I have edited the /etc/apt/sources.list  and replaced hoary by breezy.

I haven't installed any application on this one. 
I tried to install the Yahoo Messenger for Debian package, but there were some dependency problems.

Now, when I do a 

```

apt-get dist-upgrade

```

I get the following errors:

```


>root@copperskull:/home/amit # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ymessenger: Depends: libgdk-pixbuf2 (>= 0.13.0) but it is not installable
              Depends: libglib1.2 (>= 1.2.0) but it is not installable
              Depends: libgtk1.2 (>= 1.2.0) but it is not installable
              Depends: libssl0.9.6 but it is not installable
E: Unmet dependencies. Try using -f.

```


Moreover, when I do a 

```

apt-get -f dist-upgrade

```

I get a long list of errors. I have only quoted an excerpt to let you know what all the errors look like.  :)


```


Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package li
root@copperskull:/home/amit # st http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
Extracting templates from packages: 83%W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)


```

And it goes on and on for sometime...until it is all done.

---

### Post by Manny C on 2005-11-01
[quote=duffmckagan]I have Kubuntu 5.04 Hoary Hedgehog installed on my computer.

I have edited the /etc/apt/sources.list  and replaced hoary by breezy.
[/quote] 
Please post your sources.list file.

[quote=duffmckagan]
I haven't installed any application on this one. 
I tried to install the Yahoo Messenger for Debian package, but there were some dependency problems.
[/quote] 
Try
```
 sudo apt-get check 
``` 
[quote=duffmckagan]
Now, when I do a 
```

apt-get dist-upgrade

``` 
I get the following errors:

```


>root@copperskull:/home/amit # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ymessenger: Depends: libgdk-pixbuf2 (>= 0.13.0) but it is not installable
              Depends: libglib1.2 (>= 1.2.0) but it is not installable
              Depends: libgtk1.2 (>= 1.2.0) but it is not installable
              Depends: libssl0.9.6 but it is not installable
E: Unmet dependencies. Try using -f.

``` 

Moreover, when I do a 

```

apt-get -f dist-upgrade

``` 
I get a long list of errors. I have only quoted an excerpt to let you know what all the errors look like.  :)


```


Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package li
root@copperskull:/home/amit # st http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
Extracting templates from packages: 83%W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)


``` 
And it goes on and on for sometime...until it is all done.[/quote] 

First, are you prefacing all of your apt-get commands with sudo? If not, don't expect apt-get to do anything for you.

Second, try
```
 sudo apt-get update 
``` before you try
```
  sudo apt-get dist-upgrade 
``` 
But first, please post your sources.list file. This would be muchly appreciated. ;)

---


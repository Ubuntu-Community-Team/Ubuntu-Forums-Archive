---
title: "Unable To Update"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by gmseed on 2011-09-15
I just downloaded the latest v11, burnt to a CD and installed; i.e. this a new installation of Ubuntu.

However, if I go to the Update Manager and try and update it fails; I've pasted the content from "details" below.

I also tried installing OpenOffice and Skype and both these failed to install too.

Does anyone know what's wrong?

Graham

====

installArchives() failed: 
Extract templates from packages: 12%%
Extract templates from packages: 25%%
Extract templates from packages: 38%%
Extract templates from packages: 50%%
Extract templates from packages: 63%%
Extract templates from packages: 76%%
Extract templates from packages: 88%%
Extract templates from packages: 100%%

Preconfiguring packages ...


Extract templates from packages: 12%%
Extract templates from packages: 25%%
Extract templates from packages: 38%%
Extract templates from packages: 50%%
Extract templates from packages: 63%%
Extract templates from packages: 76%%
Extract templates from packages: 88%%
Extract templates from packages: 100%%

Preconfiguring packages ...


Extract templates from packages: 12%%
Extract templates from packages: 25%%
Extract templates from packages: 38%%
Extract templates from packages: 50%%
Extract templates from packages: 63%%
Extract templates from packages: 76%%
Extract templates from packages: 88%%
Extract templates from packages: 100%%

Preconfiguring packages ...

Setting up tzdata (2011g-0ubuntu0.11.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128

No apport report written because MaxReports is reached already
Errors were encountered while processing:

 tzdata

Setting up tzdata (2011g-0ubuntu0.11.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128

---

### Post by pytheas22 on 2011-09-15
From a little googling it seems that you're affected by [this bug]("https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/442941").  The solution appears to be either to try updating Ubuntu again (apparently it works on the second try), or if that still fails, make sure the permissions on your /var/cache/debconf/config.dat are correct by running:
```

sudo chmod 0644 /var/cache/debconf/config.dat
```

Then update from the command line with:
```

sudo apt-get update
sudo apt-get upgrade
```

After this the problem should not recur again (at least according to what I read in the bug report...I have not dealt with this issue personally).

---

### Post by gmseed on 2011-09-15
Hi pytheas22

Thanks for your reply. I did what you said and it worked fine without a complete reinstall. I also installed Skype after an update/upgrade and that worked fine too.

Cheers

Graham

---


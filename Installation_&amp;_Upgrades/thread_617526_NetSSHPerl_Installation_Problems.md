---
title: "Net::SSH::Perl Installation Problems"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by tself on 2007-11-19
Hi,

Ubuntu 6.06 LTS

Does anybody have any instructions for installing the Net::SSH::Perl module so as to start an SSH session from within a perl script? (Note: i don't mean Net::SSH, this is a perl wrapper and can be downloaded from the respositories)

I've looked everywhere and tried the perl CPAN install but this fails with loads and loads of dependency errors. I've spent two days on this so far and havent got anywhere so i'm clearly going about it the wrong way, my searches in google don't reveal any of the same issues.

Thanks

---

### Post by mostafaberg on 2008-01-28
You can try downloading YUM, then install it using YUM

sudo apt-get install yum
sudo yum install perl-Net-SSH-Perl

Yum is broken in my ubuntu 7.10 and im too lazy to workaround that now !

but maybe yours will work !

you can also try to get it using CPAN, did you try that ?

first get into cpan:
sudo perl -MCPAN -e shell

you can install it now:
install Net::SSH::Perl

I've got the same issue here, I'm trying to run SSHatter and I'm going insane :D

I think it should work easily for you
keep me updated !

---

### Post by gumispl on 2008-02-15
I downloaded it from:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Flibn%2Flibnet-ssh-perl-perl%2Flibnet-ssh-perl-perl_1.30-1_all.deb&md5sum=a556760cfa4905f1eb4b2108fc298816&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Flibn%2Flibnet-ssh-perl-perl%2Flibnet-ssh-perl-perl_1.30-1_all.deb&md5sum=a556760cfa4905f1eb4b2108fc298816&arch=all&type=main)

---


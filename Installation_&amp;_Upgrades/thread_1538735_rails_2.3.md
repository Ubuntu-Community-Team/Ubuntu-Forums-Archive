---
title: "rails 2.3"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by bluto on 2010-07-25
Hi,

I just upgraded to Kubuntu Lucid and installed rails 2.3.8 via gems for a project requiring features in that release:

*** LOCAL GEMS ***

actionmailer (2.3.8 
actionpack (2.3.8
activerecord (2.3.8
activeresource (2.3.8
activesupport (2.3.8
rack (1.1.0
**rails (2.3.8 **
rake (0.8.7

The rails command fails unless I include the full path, i.e.:

[INDENT]**/var/lib/gems/1.8/bin/rails** [/INDENT]


I tried a symlink to /var/lib/gems/1.8/bin/rails:

[INDENT]**sudo ln -s /var/lib/gems/1.8/bin/rails rails**[/INDENT]


and got:

[INDENT]**ln: creating symbolic link `rails': File exists**[/INDENT]


But entering rails command still fails with:

[INDENT][B]The program 'rails' is currently not installed.  You can install it by typing:
sudo apt-get install rails[/B]
[/INDENT]

I have never had any issues with using gem to install rails before this release.  What am I missing?

Thanks,
Bluto

---


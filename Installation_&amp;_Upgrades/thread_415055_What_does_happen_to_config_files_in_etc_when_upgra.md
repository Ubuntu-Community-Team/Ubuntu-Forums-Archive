---
title: "What does happen to config files in /etc when upgrading from Edgy to Feisty?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by astronic on 2007-04-20
Dear Forum,

when updating from Edgy to Feisty using update-manager, what happens in the two following scenarios?


1) A config file in /etc is by default different in Edgy and Feisty but has not been modified by me.

2) I edited a config file in /etc myself.


In case 1) I would like the config file to be just overwritten by the Feisty version. Does update-manager take care of that?

In case 2) I don't see an alternative but to review things manually. But how does this work? Will update-manager put the new config files with a special ending in /etc and leave the current ones untouched, like it works with "apt-get dist-upgrade"? Will it just keep the new config files from being installed at all? Will it overwrite my modified config files?


Thanks in advance!

Regards,
Stefan

PS.: I think this topic should be really covered in the upgrade notes, since there is no way how update-manager can reliably perform the task fully automatically without the risk of breaking something.

---

### Post by az on 2007-04-20
When you install a package by hand, and the config file has been modified since the package was installed, it will ask you.  The default action is to keep the existing configuration, since you don't want your copmuter to stop working the way you had it working just because you upgrade.  The configs are supposed to be compatible in general.  When one version of an app changes dramatically, this is usually handled by the upstream version number change (Ex /etc/apache/ and /etc/apache2/.

I would assume the update manager would do the sensible thing:  Update to the new version if you are using the default, and keep the current version if you changed it.

Usually, any problems with incompatible configurations are found by the many apps that save personal configurations in your home drive.  I have had to fix problems by hand by deleting some dotfiles in my home drive (Like deleting all .gnome and .gnome2 directories to fix a broken desktop)

---

### Post by cbravo on 2007-04-20
For me, this wasn't a problem. If I changed files, it asked what to do. Unchanged files were overwritten without asking. 

I had about 10 changed files in /etc. Remember, you only need to change the config file if the application actually needs a different configuration. Whether this is the case, can usually be seen by looking at  the differences.

---

### Post by astronic on 2007-04-20
> **cbravo said:**
> For me, this wasn't a problem. If I changed files, it asked what to do. Unchanged files were overwritten without asking. 
Thank you very much for you answer (and also to az of course): So I get it right that update-manager is asking interactively in such cases?

And what happens to packages that are obsolete and thereby get removed? Are their config files purgued by update-manager?

Thanks again!

Regards,
Stefan

---

### Post by az on 2007-04-20
> **astronic said:**
> 
And what happens to packages that are obsolete and thereby get removed? Are their config files purgued by update-manager?

Thanks again!

Regards,
Stefan

Removing a file leaves behind the config files as well as the package manager configurations that may have been modified.  Purging the file will remove the package manager configs as well as removing the file.  In both cases, you still have to remove the configs in your home drive and in /etc by hand.

---


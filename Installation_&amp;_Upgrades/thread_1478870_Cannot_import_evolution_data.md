---
title: "Cannot import evolution data"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Docaltmed on 2010-05-10
I've recently upgraded to 10.04. I'm trying to import my evolution data using the following instructions. Everything seems to work ok, but when I start evolution up, it continues to act as a new installation. What do I do?

> You have an Evolution installation in one home directory and you want to duplicate that configuration in a new home directory. This may involve moving your data from one computer to another. Keywords: migration, user data, new partition, new computer, new home directory

   1. Completely shut down Evolution on the old machine/home directory:
         1. evolution --force-shutdown 
   2. If you've used Evolution on the new computer/home directory, remove its config files:
         1. evolution --force-shutdown
         2. cd $NEWHOME; rm -rf .evolution .gnome2_private/Evolution .camel_certs 
   3. Copy the following from the old home directory to the new home directory:
         1. cp -R $OLDHOME/.evolution $NEWHOME
         2. cp -R $OLDHOME/.gnome2_private/Evolution $NEWHOME/.gnome2_private/Evolution # if the old Evolution version is 2.12 or earlier
         3. cp -R $OLDHOME/.camel_certs $NEWHOME 
   4. Dump your Evolution settings stored in GConf by running (on the old machine/home directory)
         1. gconftool-2 --dump /apps/evolution > some-file.xml 
   5. If for some reason you cannot dump your Evolution settings in GConf (e.g. no access to the old system), copying the data (cp -R oldComputer:$OLDHOME/.gconf/apps/evolution newComputer:$NEWHOME/.gconf/apps/evolution) will do as well, but make sure that this is done while Gnome and the GConf daemon are not running, see below.
   6. On the new computer/home directory, make sure you are not running gconf (by ps ax | grep gconf for example; you normally have to leave Gnome and then run gconftool-2 --shutdown).
   7. Import those settings by running
         1. gconftool-2 --load some-file.xml 
   8. Log in to gnome again 

---

### Post by texpat on 2010-05-10
Not sure I understand this properly. Those instructions seem very complicated.

In evolution, in the 'file' menu you have 'backup settings'. This creates a tar.gz file with all the relevant information, including mail account settings, the actual emails and so on.

You can then 'restore settings' from the menu, or while the new install of evolution sets itself up.

---

### Post by Docaltmed on 2010-05-10
I made a backup of my home folder before upgrading to Lucid, but did not make a separate backup of evolution data specifically. For unknown reasons, restoring the home folder in its entirety caused problems with Lucid, so I've had to restore it all piece by piece.

Thus, I do not have an evolution-specific backup file, and am having to work off the original files from my home folder.

I can't understand why, after loading the settings kml file, evolution still pretends that this is a new installation.

---

### Post by Docaltmed on 2010-05-11
anybody?

---

### Post by Docaltmed on 2010-05-11
I tried uninstalling and reinstalling, and that didn't work.

So I just went ahead with the setup process, re-entered all of my account information, and when I finished, Evolution started with all of my old email, accounts, memos and calendar entries intact.

Go figure. I hope this helps anyone else with the same problem.

---

### Post by klyndt on 2010-12-19
I was able to copy back my .evolution folder and my .gconf/apps/evolution folders successfully.  The trick is I went into system monitor and killed anything evolution.  There is an evolution-data-server and a evolution-exchange-storage that are running all the time. Once I nuked those and did the copy, the next time I started evolution, everything was back. Hope that helps.

---


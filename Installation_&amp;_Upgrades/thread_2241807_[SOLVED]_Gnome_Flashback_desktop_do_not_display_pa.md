---
title: "[SOLVED] Gnome Flashback desktop do not display panel after ugrade to 14.04"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by danemaslen on 2014-08-28
Hardware: Dell Latitude 2110
Current Ubuntu version: 14.04
Previous version 12.04

In 12.04 I used Gnome Classic (No Effects) as my desktop environment.

Today I accepted the 14.04.1 upgrade.  It proceeded without any apparent errors.  Following the reboot the login screen appeared correctly, I logged in successfully, and was pleased to see that my desktop environment appeared to be unchanged (in 12.04 I had Gnome Classic configured with just a top panel and that was indeed how my desktop environment appeared at this stage).  There were, however, some error messages (something I'm accustomed to after Ubuntu upgrades), so I thought it would be wise to run Update Manager to see if there were any updates available.  It was at this stage that I noticed the first oddity: Update Manager didn't appear in its usual place under System Tools — Administration.  Indeed it didn't appear anywhere, so I had to run it from a terminal window.  It requested that I do a partial upgrade.  This wasn't something I'd ever encountered on previous upgrades, but I did so, rebooted, and then encountered problems with the Gnome Flashback desktop environments.

At the login screen I am offered four choices:
[LIST]
[*]GNOME
[*]GNOME Flashback (Compiz)
[*]GNOME Flackback (Metacity)
[*]Ubuntu (Default)
[*]
[/LIST]
As far as I can tell (I have no idea how the new GNOME desktop environment is supposed to work and I have always minimised my exposure to Unity) GNOME and Ubuntu (Default) work correctly, but the two GNOME Flashback options just display the desktop, i.e. no top panel.

I have been rummaging in search of a solution.  The thread
[INDENT][http://askubuntu.com/questions/459551/gnome-flashback-panels-not-starting-in-ubuntu-14-04](http://askubuntu.com/questions/459551/gnome-flashback-panels-not-starting-in-ubuntu-14-04) [/INDENT]
seemed promising but when I tried its suggestion of running gnome-panel, I got the message
[INDENT]Cannot register the panel shell: there is one already running[/INDENT]

Any ideas?  It occurs to me that maybe my desktop environment configuration has been corrupted such that it specifies no panels.  While awaiting a reply to this post, I shall attempt to refresh my memory about how the desktop environment configuration can be handled from the command line.

---

### Post by danemaslen on 2014-08-28
> **danemaslen said:**
> It occurs to me that maybe my desktop environment configuration has been corrupted such that it specifies no panels.  While awaiting a reply to this post, I shall attempt to refresh my memory about how the desktop environment configuration can be handled from the command line.

Using dconf-editor on both the 14.04 system and a 12.04 system, I suspect I have found the cause of the problem, but not the solution.

On the 12.04 system the schema org.gnome.gnome-panel.layout has object-id-list (['indicators','object-0',etc]) and toplevel-id-list ('[top-panel]') plus objects and toplevels items.

On the 14.04 system the schema org.gnome.gnome-panel.layout has null values for object-id-list and toplevel-id-list, and lacks objects and toplevels items.

So I think my question now becomes "How do I get my top panel back?"

---

### Post by kansasnoob on 2014-08-28
I made some notes here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

Be sure and look at #1 under **Challenges and Known Issues**.

If neither 1(a) or 1(b) works then see if the panels appear OK in a guest session.

Oh, you might also want to run the following command to check for missing dependencies:

```
sudo apt-get -f install
```

---

### Post by danemaslen on 2014-08-28
> **kansasnoob said:**
> I made some notes here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

Be sure and look at #1 under **Challenges and Known Issues**.

If neither 1(a) or 1(b) works then see if the panels appear OK in a guest session.

Thanks (and while I remember it, thanks for your posting about configuring Gnome Classic in 12.04 - it was very useful when I upgraded from 10.04 18 months ago).  In the process of trying to do 1(a) I discovered what the problem was: $HOME/.config/dconf/user was owned by root!  Presumably, given that all was well before the partial upgrade, something in the partial upgrade changed the file's ownership, but what and why is anyone's guess.

Having corrected the ownership of $HOME/.config/dconf/user, I now have my top panel back and as far as I can see it is as it was under Gnome Classic in 12.04 other than that Update Manager is still missing from System Tools — Administration on the Main Menu.  I have now manually added it back in.

---


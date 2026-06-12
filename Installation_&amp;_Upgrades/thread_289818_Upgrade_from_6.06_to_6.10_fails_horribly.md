---
title: "Upgrade from 6.06 to 6.10 fails horribly"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Mr. Blue on 2006-10-31
[B]My desktop (now half Drake, half Edgy) is stuck in an inconsistant state that I can't seem to resolve.  Ran the update-manager as documented, downloaded all required files, started the install.  However, partway through, it just craps out.  Half of my apps are edgy, the rest are drake, and most of the system is unusable.

If I try to run update-manager -c again, I get this:[/B]

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 25, in ?
    import pygtk
ImportError: No module named pygtk
[B]
If I run an apt-get upgrade -u, I get this:[/B]

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  courier-authlib-userdb: Depends: courier-authlib but it is not installed
                          Depends: courier-authlib (>= 0.58) but it is not installed
  courier-base: Depends: courier-authlib but it is not installed
E: Unmet dependencies. Try using -f.

**Following the suggestions, I try apt-get -f install courier-authlib, and get this:**

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  courier-authdaemon
The following NEW packages will be installed:
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
949 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 164kB of additional disk space will be used.
Do you want to continue [Y/n]?
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_CA:en",
        LC_ALL = "",
        LANG = "en_CA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
root@zeus:/etc/apt# Errors were encountered while processing:
 courier-authdaemon

**Anybody got any ideas?  I'd prefer to avoid a reinstall.  Note I can't run the update-manager from the icon, as gksudo does not seem to accept my password any longer.**

---

### Post by John.Michael.Kane on 2006-10-31
Sorry to say but in cases where the dist-upgrade has started to install edgy,and does not finish your only option is a clean reinstall.

---

### Post by hardrock on 2006-11-05
> **SD-Plissken said:**
> Sorry to say but in cases where the dist-upgrade has started to install edgy,and does not finish your only option is a clean reinstall.

I don't think that this is true.

I had a lot of serious problems too during upgrade, but finally managed to upgrade successfully. I will post here what I did, maybe it helps someone else.

First of all, I'm recovering all this from memory, so I hope I'm not missing something. Also: Never enter "apt-get clean" once the download is complete! I didn't really know about this command, it was suggested somewhere and in the end I had to download all the files again.

I did the upgrade to Edgy using updatemanager -c, the download went successfully, but when it came to installing httpd, the upgrade aborted since Apachce was still running on a desired port. So I stopped Apache and tried to start the upgrade again. But whatever I did, whether it was the updatemanager, apt-get -f install or anything else: I always got an "dpkg returned error" message and the process aborted.

The solution to this problem was to recover the file /var/lib/status-old. You have to backup /var/lib/status and rename the status-old to status.

After that, apt-get update and apt-get -f install worked for me. When I typed apt-get dist-upgrade to recommence the upgrade to Edgy, it went fine for some time, but then it aborted returning some error about postgresql-8.1. I tried a few things, and once I typed apt-get remove postgresql-8.1 the setup suddenly went on, skipping this package.

In the end the update went successfully, some files where still broken that I reinstalled manually using apt-get install. And now I'm happy on a fresh Edgy without having had to reinstall :)

---

### Post by Kevuntu on 2007-10-21
I have the same problem!
My Distribution Upgrade isn't finished, but I'm having errors and gnome (synaptic) doesn't accept my password. Only terminal does. Rebooting is getting scary!

Here's what I did using Dapper 6.06 on a IBM Thinkpad R31:
1-I entered **gksudo "update-manager -c -d"** (including the quotes) in terminal.
2-The download was long, but without errors.
3-Then, I got an error in the terminal section below the progress bar in the Distribution Upgrade window about locales : (it was not a popup message)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
LANGUAGE = "en_CA:en",
LC_ALL = "",
LANG = "en_CA.UTF-8"
are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
4-The process continued and everything seemed OK until I got a popup message telling me that acpi and acpi-support failed to install or something.
5-At this point, I'm getting REALLY scared because synaptic and other applications started by gnome tell me that my password is incorrect.:( Only terminal accepts it.

Now, Ubuntu is still installing the upgrades and will finish in about two hours.
I'm really scared about rebooting because what will happen if it tells me that my password is wrong on login?

Please help. Thanks in advance. :)

---


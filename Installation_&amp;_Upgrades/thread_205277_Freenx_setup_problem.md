---
title: "Freenx setup problem"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by krisravn on 2006-06-28
I have just installed freenx and I have edit the configuration file I want to edit. But when I try to run nxsetup, I got the following error:

```

root@serv057:/usr/lib/nx# nxsetup
------> You did select no action.
        FreeNX guesses that you want to _install_ the server.
        Type "y" to abort the installation at this point in time.
        "N" is the default and continues installation.
        Use "/usr/sbin/nxsetup --help" to get more detailed help hints.

 Do you want to abort now? [y/N]

------> It is recommended that you use the NoMachine key for
        easier setup. If you answer "y", FreeNX creates a custom
        KeyPair and expects you to setup your clients manually.
        "N" is default and uses the NoMachine key for installation.

 Do you want to use your own custom KeyPair? [y/N]
Setting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.
/usr/lib/nx/nxloadconfig: line 498: strings: command not found
Error: Could not find 1.5.0 version string in nxagent. NX 1.5.0 backend option must be used with 1.5.0 OSS components.
/usr/lib/nx/nxloadconfig: line 501: strings: command not found

  Errors occured during config check.
  Please correct the configuration file.

root@serv057:/usr/lib/nx#

```

It's probably a question about, I use a different version of nxagent then it expect, but I pretty sure that it should be 1.5.0. But have to check the version of nxagent and have to solve the problem?

Regards
Kristoffer

---

### Post by allnameswereout on 2006-06-28
Its a dependancy issue in the package. Contact the maintainer.

Here's the issue

*/usr/lib/nx/nxloadconfig: line 498: **strings: command not found***

You need to install
*[http://packages.ubuntu.com/dapper/devel/binutils](http://packages.ubuntu.com/dapper/devel/binutils)*

Do this by doing

*sudo apt-get install binutils*

And retry what you were doing.

---


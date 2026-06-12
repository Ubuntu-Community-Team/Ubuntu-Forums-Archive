---
title: "do-release-upgrade error (10.04.04 -&gt; 12.04.01)"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by geekswordsman on 2012-10-09
Hello all -

I have a client with a server running 10.04.04 Lucid.  As this is a production box for them I've left it alone - until recently when the software they're running has new updates.  I figured while I was in there updating things for them, I'd get them up to date on the OS while I was at it.  This isn't my first upgrade from Lynx to Precise; I have several other boxes that required this exact upgrade and they all went off without a hitch.

This is a pretty plain-jane box, default install with LAMP and SSH.

Unfortunately things aren't going so smoothly here and no amount of searching has gotten me a solution that fixes the issue.

I ran through the normal routine:
apt-get update && apt-get upgrade
apt-get install update-manager-core
do-release-upgrade

Everything looks good until "do-release-upgrade", which gives me the following error:
```
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 1
Debug information: 


gpg: Signature made Mon 13 Aug 2012 04:23:33 PM EDT using DSA key ID 437D05B5
gpg: /tmp/tmpH92lpk/trustdb.gpg: trustdb created
gpg: BAD signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server. 

```

Here is the output of apt-key finger:
```
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
      Key fingerprint = 6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
      Key fingerprint = C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024R/386B7051 2009-01-19
      Key fingerprint = 0497 0465 5DF2 74CC 4DE6  03AD C95C 0E19 386B 7051
uid                  Launchpad PPA for SchoolTool Owners
```

For funsies, I backed up /etc/apt/trusted.gpg, removed 437D05B5, and tried to add it again:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 630239CC130E1A7FD81A27B140976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 630239CC130E1A7FD81A27B140976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

Server is not behind a proxy.  All updates have been going throughout without a problem.

Please be aware, *backing up and doing a fresh install is not an option on this machine as it is hosted at a remote client site.*  I'm hoping for a solution that will get things upgraded remotely via ssh, worse case scenario this poor box has to stay on Lucid Lynx!

Thanks very much for the help.

---

### Post by eric0043 on 2012-10-18
Ran into the same problem.  After I edited /etc/apt/sources.list everything worked. I simply removed the 'de.' 

Before:

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid main restricted

After:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted

---


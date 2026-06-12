---
title: "&quot;Failed Upgrade tool signature&quot; when using do-release-upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by mmcev106 on 2007-10-21
First I got this:

```
root@Bunter:/# do-release-upgrade 
Checking for a new ubuntu release
current dist not found in meta-release file
No new release found
root@Bunter:/# 
```

Fixed that via the info at this thread:
[http://ubuntuforums.org/showthread.php?p=3466585](http://ubuntuforums.org/showthread.php?p=3466585)

But, why not just include the meta-release file in update-manager-core or something?

Now I have this problem:

```
root@Bunter:/# do-release-upgrade 
Checking for a new ubuntu release
Failed Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting '/tmp/tmpA-amtI/gutsy.tar.gz'
authenticate '/tmp/tmpA-amtI/gutsy.tar.gz' against '/tmp/tmpA-amtI/' 
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information: 

gpg: WARNING: unsafe permissions on homedir `/tmp/tmpA-amtI'

gpg: /tmp/tmpA-amtI/: read error: Is a directory
gpg: verify signatures failed: eof

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server. 
root@Bunter:/# 
```

Anybody know what's up?

Thanks,
Mark

---

### Post by Lesterchakyn on 2007-10-23
As weird as this may sound, I think it goes with the gpg personal keys not being created before the update.

I just ran gpg (no arguments), and it created the personal keys.

After that, I could run the upgrade with no problems.

---

### Post by mmcev106 on 2007-10-25
```

root@Bunter:~# gpg
gpg: Go ahead and type your message ...

gpg: no valid OpenPGP data found.
gpg: processing message failed: eof
root@Bunter:~#
```

I get the impression I'm supposed to paste a key in here and hit Ctrl-D, but what key?  Am I supposed to generate one?

---

### Post by mmcev106 on 2007-10-25
Figured it out.  It was a truncated '/var/lib/update-manager/meta-release' file, which makes perfect sense considering the last line of that files is the web address of the gutsy.tar.gz.pgp file.

I had to create the 'meta-release' file like I explained in my first post, and apparently I'm stupid and can't copy and paste correctly.  Which begs the question, shouldn't the 'meta-release' file be included in update-manager-core to prevent idiots like me from screwing it up?

---

### Post by fst_odl on 2008-01-11
Currently I'm not able to acces the file [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg) - it seems unreadable....I tried it via Firefox and wget.

---


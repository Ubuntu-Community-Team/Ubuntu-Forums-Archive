---
title: "ubuntu 10.04  hash sum mismatch"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by tock on 2010-10-01
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/uno-libs3_1.6.1+OOo3.2.1-6ubuntu2~10.04.1_i386.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_3.2.1-6ubuntu2~10.04.1_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_3.2.1-6ubuntu2~10.04.1_i386.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.2.1-6ubuntu2~10.04.1_i386.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_3.2.1-6ubuntu2~10.04.1_all.deb  Hash Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_3.2.1-6ubuntu2~10.04.1_all.deb  Hash Sum mismatch
Failed to fetch http://archive.getdeb.net/ubuntu/pool/apps/g/gimp/gimp_2.6.10-1~getdeb1_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I've tried the suggested fix with no improvements..  Also tried rebuilding the source.list and changing to the default server for updates.  Nothing has worked.
How do I get passed this?

Thanks

---

### Post by sikander3786 on 2010-10-01
Go to System > Administration > Software Sources and select Main Server.

US servers are down today, I have heard a few times today on these forums.

---

### Post by tock on 2010-10-01
Tried the default server. Now unable to update do to sig key errors.  Tried deleting and using ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 40976EAF437D05B5 40976EAF437D05B5 40976EAF437D05B5 40976EAF437D05B5

```

The result was
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 40976EAF437D05B5 40976EAF437D05B5 40976EAF437D05B5 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: no ultimately trusted keys found
gpg: Total number processed: 5
gpg:               imported: 1
gpg:              unchanged: 4

```

This did not help.  Still unable to update repositories.

Thanks for replying!

---

### Post by sikander3786 on 2010-10-01
What is the output of apt-get update for now?

---

### Post by kumarnat on 2010-10-13
I have a similar problem, I have linux 10.04  and upgrade gives me the following error

Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.bz2)  Hash Sum mismatch

My updates are from the main server..

Any help appreciated.

---

### Post by sikander3786 on 2010-10-14
First of all try

```
sudo apt-get clean
```

```
sudo apt-get update && sudo apt-get upgrade
```

Some ISPs cache the packages and errors like these are reported then. If the above commands don't work, try

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

and again

```
sudo apt-get update && sudo apt-get upgrade
```

If it still doesn't work,

```
sudo apt-get update -o Acquire::BrokenProxy=true
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ahmd6 on 2011-04-05
I tried all these steps and at the end I got this response


"Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/pool/main/g/geoip/geoip-database_1.4.7~beta5+dfsg-1_all.deb](http://ubuntu.qualitynet.net/ubuntu/pool/main/g/geoip/geoip-database_1.4.7~beta5+dfsg-1_all.deb)  Hash Sum mismatch
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/pool/main/e/example-content/example-content_43_all.deb](http://ubuntu.qualitynet.net/ubuntu/pool/main/e/example-content/example-content_43_all.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

Is there anything else to do? any other suggestion?
Thanks

---

### Post by sikander3786 on 2011-04-06
> **ahmd6 said:**
> I tried all these steps and at the end I got this response


"Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/pool/main/g/geoip/geoip-database_1.4.7~beta5+dfsg-1_all.deb](http://ubuntu.qualitynet.net/ubuntu/pool/main/g/geoip/geoip-database_1.4.7~beta5+dfsg-1_all.deb)  Hash Sum mismatch
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/pool/main/e/example-content/example-content_43_all.deb](http://ubuntu.qualitynet.net/ubuntu/pool/main/e/example-content/example-content_43_all.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

Is there anything else to do? any other suggestion?
Thanks
Did you change your update server to "Main" from Software Center > Edit > Software Sources?

---

### Post by ahmd6 on 2011-04-16
sikander3786
No I did NOT. thanks for taking the time for answering my question. Actually my problem was solved few  days ago.

I don't know how or why? I just happened few days ago. an update notice came and every thing went smoothly. the upgrade went through and I am all new and fresh 10.10

Any way I am gonna change it to main as per you recommendation

Thanks

---

### Post by sikander3786 on 2011-04-17
> **ahmd6 said:**
> sikander3786
No I did NOT. thanks for taking the time for answering my question. Actually my problem was solved few  days ago.

I don't know how or why? I just happened few days ago. an update notice came and every thing went smoothly. the upgrade went through and I am all new and fresh 10.10

Any way I am gonna change it to main as per you recommendation

Thanks
You are Welcome.

Sometimes some mirrors are not well maintained and hash mismatches are common. Main server works well in almost all the cases however user load might decrease its speed at times.

---


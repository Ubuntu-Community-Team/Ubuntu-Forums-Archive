---
title: "Update Errors. On gutsy"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by computer_guy98 on 2008-07-10
Every time I click Install Updates I get this message.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ar/language-pack-ar_7.10+20080704_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ar/language-pack-ar_7.10+20080704_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

And it says it about every source.

---

### Post by iaculallad on 2008-07-10
> **computer_guy98 said:**
> Every time I click Install Updates I get this message.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ar/language-pack-ar_7.10+20080704_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-ar/language-pack-ar_7.10+20080704_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

And it says it about every source.

Post whatever displays when you issue the command below using the terminal:

```
cat /etc/hosts
```

---

### Post by computer_guy98 on 2008-07-11
> **iaculallad said:**
> Post whatever displays when you issue the command below using the terminal:

```
cat /etc/hosts
```


mulder@AMMO-533:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       AMMO-533

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
mulder@AMMO-533:~$

---

### Post by iaculallad on 2008-07-11
/etc/hosts file looks good.

Open your terminal and issue the commands below:

```
unset http_proxy
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by computer_guy98 on 2008-07-11
Thank you. that fixed all but ten of them.


These ten are still not working.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-15-generic_2.6.22-15.54_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-15-generic_2.6.22-15.54_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.22/linux-ubuntu-modules-2.6.22-15-generic_2.6.22-15.39_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.22/linux-ubuntu-modules-2.6.22-15-generic_2.6.22-15.39_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.3.3+0.4-0ubuntu0.7.10.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.3.3+0.4-0ubuntu0.7.10.2_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-15_2.6.22-15.54_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-15_2.6.22-15.54_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-15-generic_2.6.22-15.54_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-15-generic_2.6.22-15.54_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.22.15.22_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.22.15.22_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.22.15.22_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.22.15.22_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/linux-restricted-modules-2.6.22-15-generic_2.6.22.4-15.11_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/linux-restricted-modules-2.6.22-15-generic_2.6.22.4-15.11_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.22.15.22_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.22.15.22_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu0.7.10.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu0.7.10.1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by upchucky on 2008-07-11
127.0.0.1 is your own machine, you need to edit your sources, place a # in front of each of those lines. then try again, I had to switch my sources in package manager to main, then back to united states not long ago to get them all working.

if it completes with those sources ignored you are good to go.

---

### Post by oldsoundguy on 2008-09-01
found this thread .. have a similar problem only the one I can't open for update/upgrade is this one:
Could not connect to ubuntu.org.ua:80 (91.193.124.193). - connect (111 Connection refused)

This is NOT listed in my sources and I am unable to enter the link into the sources.  
I have the ubunto.org.ua/getdeb/ though.

---

### Post by oldsoundguy on 2008-09-02
I feel the need to BUMP!  LOL

---

### Post by Michl on 2008-09-11
> **upchucky said:**
> 127.0.0.1 is your own machine, you need to edit your sources, place a # in front of each of those lines. then try again, I had to switch my sources in package manager to main, then back to united states not long ago to get them all working.

if it completes with those sources ignored you are good to go.

Where do you do this.  Have the same problem.

---

### Post by iaculallad on 2008-09-11
> **Michl said:**
> Where do you do this.  Have the same problem.

You do it in the Software Sources. System->Administration->Software Sources, under "Ubuntu Software" tab. Change your repository download server to point to "Main Server"

---


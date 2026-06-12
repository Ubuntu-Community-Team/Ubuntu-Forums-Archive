---
title: "cant update my ubuntu &quot;W: GPG error:&quot;"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by waleedakleh on 2010-12-05
when i click on the check button in the update manager this error message box comes up after download packet information
> W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
i also tried "sudo apt-get update" in terminal, this came up
> Reading package lists... Done
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466

i don't know what is the problem! anyone got a solution?
any help would be appreciated

---

### Post by drs305 on 2010-12-05
Run this command to add the key for the repository:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 49A120FD1135D466 

```

The repositories need verification to ensure you are getting a safe download. By adding the 'key' to the repository you are helping ensure your download is coming from an authorized site.

---

### Post by waleedakleh on 2010-12-05
> **drs305 said:**
> Run this command to add the key for the repository:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 49A120FD1135D466 

```

The repositories need verification to ensure you are getting a safe download. By adding the 'key' to the repository you are helping ensure your download is coming from an authorized site.

thanks but now i am getting this error
> 
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures were invalid: KEYEXPIRED 1282402468

---

### Post by drs305 on 2010-12-05
I have never had that message before. Open Synaptic or Software Sources, Settings, Repositories, Authentication tab. Find the seveas listing and select "Remove". Then run the import key command again.

---

### Post by waleedakleh on 2010-12-05
> **drs305 said:**
> I have never had that message before. Open Synaptic or Software Sources, Settings, Repositories, Authentication tab. Find the seveas listing and select "Remove". Then run the import key command again.

did what you told me:
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 49A120FD1135D466
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 49A120FD1135D466
gpg: requesting key 1135D466 from hkp server keyserver.ubuntu.com
gpg: key 1135D466: public key "Dennis Kaarsemaker (Package signing key) <dennis@kaarsemaker.net>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

and the update manager gave me:
> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://jo.archive.ubuntu.com](http://jo.archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://jo.archive.ubuntu.com](http://jo.archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures were invalid: KEYEXPIRED 1282402468
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by drs305 on 2010-12-05
That is a different key for a different repository, so you would run the same command but replace the alphanumeric at the end:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 A040830F7FAC5991
```

As you can see, you can combine keys in the command. I also see the EXPIRED key message. Did you try to delete that one first?

---

### Post by sgosnell on 2010-12-05
In the meantime, that is only a gpg error, telling you that there is no valid key on your machine for the repository.  You will still get the updates if you continue.  It's just a warning, not a fatal error.  There is no requirement for having a key for any repository, it's just a security precaution.  Installing keys is a good idea, but lack of one shouldn't prevent you from doing an upgrade, as long as you know the repository is the correct one.

---

### Post by waleedakleh on 2010-12-05
i am back to this
> W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures were invalid: KEYEXPIRED 1282402468
tried 
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1282402468
gave me 
> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 1282402468
gpg: "1282402468" not a key ID: skipping

---

### Post by drs305 on 2010-12-05
> **waleedakleh said:**
> i am back to this

tried 

gave me

I may have confused you a bit. That key has expired, so you wouldn't try to import that key again.
You should also be able to remove that expired key with:
```
sudo apt-key del 1282402468 
```

*sgosnell* made a good point that I should have mentioned as well.

---

### Post by waleedakleh on 2010-12-05
i see now what is the problem 
i ran "lsb_release -a"
i have Ubuntu 10.04.1 LTS thats why i cant get the 10.10 version because it is not for the LTS version yet
do i have to reinstall ubuntu with the normal version to get the 10.10?

---

### Post by sgosnell on 2010-12-06
That repository (ubuntulinux.nl) seems to be for Ubuntu 6 & 7.  I don't see anything for later versions.  Are you sure there is anything there for 10.10?  What package specifically are you trying to get?

Again, you don't have to worry about the keys, the update manager will get the updates without them, it's just a warning, not a fatal error.

---


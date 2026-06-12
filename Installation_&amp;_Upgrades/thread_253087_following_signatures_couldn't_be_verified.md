---
title: "following signatures couldn't be verified"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by cccc on 2006-09-07
hi

during the apt-get update, I get the following error:```

W: GPG error: http://people.ubuntu.com ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B0B7481B1F44842D
W: You may want to run apt-get update to correct these problems
```
to run apt-get again it doesn't help.

my /etc/apt/sources.list:```
# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://ch.archive.ubuntu.com/ubuntu dapper main restricted
deb http://ch.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://ch.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://ch.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://ch.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://ch.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
#deb http://mirror.ubuntulinux.nl dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
#deb-src http://mirror3.ubuntulinux.nl dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
#deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
#deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# Penguin Liberation Front (packages)
#deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Penguin Liberation Front (sources)
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# The Opera browser (packages)
deb http://deb.opera.com/opera etch non-free

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

## kadu
deb http://www.kadu.net/download/binary/ubuntu/repo dapper main
```

howto solve this problem ?

---

### Post by whizbaby on 2006-09-07
Perhaps the key is not valid anymore?

---

### Post by cccc on 2006-09-07
> **whizbaby said:**
> Perhaps the key is not valid anymore?

and howto get it validated ?

---

### Post by whizbaby on 2006-09-07
Somehow you'll have to get it from the server. Cannot say for your repositories, but here is an example
 [http://wiki.scribus.net/index.php/Scribus_on_Debian_GNU/Linux#Using_cryptographic_repository_signatures:](http://wiki.scribus.net/index.php/Scribus_on_Debian_GNU/Linux#Using_cryptographic_repository_signatures:)
'using cryptographic repository signatures'

---

### Post by whizbaby on 2006-09-07
Trying to be a little more helpful I typed
[http://people.ubuntu.com/~jbailey/snapshot/bzr/](http://people.ubuntu.com/~jbailey/snapshot/bzr/)
in my browser (you can click on the link). There is a file *Release.gpg*.
Together with the example you should make it. (besides you can type all of the repository adresses in your browser if you want to know what the hell's going on there)

---

### Post by satbunny on 2006-09-20
I had a similar problem. I then opened Synaptic, browsed to the relevant source entry (repositories on menu) and clicked the 'Authentication' tab and imported the new GPG key I had downloaded and saved to my drive. It failed to import and I still have the error message.

The file contained the following key, how do I get this into use for apt-get or synaptic?:

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.5 (GNU/Linux)

iD8DBQBFD7obB9xWPR9BuQcRAo/OAJ4mHVjAMU15Yfh2s8RU4arrwKmiVACfVD2q
RUHUsA7Nuk82jkZ1d7iCwEQ=
=WCmC
-----END PGP SIGNATURE-----

---

### Post by satbunny on 2006-09-20
Ah! Is that gpg file corrupt maybe?

---

### Post by whizbaby on 2006-09-20
I guess you have the key in a file
*name_of_key*.asc
go to that directory and type
**sudo apt-key add *name_of_key*.asc**
and post the error message(s).
To retrieve a key do
wget http-adress-of-key (e.g. 'http://somerepository.example/pool/repo_key.asc'(fantasy-repo))
and then *sudo apt-key add* the key.
Browse the repo for the key's adress.

---


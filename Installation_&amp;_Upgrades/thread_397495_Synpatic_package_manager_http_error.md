---
title: "Synpatic package manager http:// error"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by SpikeyB on 2007-03-30
When I reload in the synaptic package manager, I get the following error:

[http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:) 404 Not Found

followed by:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Is there any way that I can stop this happening?

Thanks for any advice.

---

### Post by zvacet on 2007-03-31
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -
```


in your case 


gpg --keyserver hkp://subkeys.pgp.net --recv-keys **58403026387EE263**
 gpg --export --armor** 58403026387EE263 **| sudo apt-key add -


```
sudo aptitude update
```

---

### Post by SpikeyB on 2007-03-31
zvacet

Thank you very much for your help.

Your information moved me forward.  Now I receive the message:

[http://wine.budgetdedicated.com/apt/dists/dapper/Release:](http://wine.budgetdedicated.com/apt/dists/dapper/Release:) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

Your help prompted me to investigate further, the options in the Synaptic Package Manager and I was able to stop the error message by removing the tick from [http://wine.budgetdedicated.com/apt/..............(binary](http://wine.budgetdedicated.com/apt/..............(binary)) in the channels.  

Admittedly, that hasn't necessarily solved my underlying problem, merely hidden it.  My knowledge isn't good enough yet, so I am satisfied with hiding the problem and I thank you for that.

---


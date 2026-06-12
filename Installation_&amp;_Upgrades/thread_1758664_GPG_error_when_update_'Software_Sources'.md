---
title: "GPG error when update 'Software Sources'"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2011-05-14
Hi,

I Go to 'Settings' in Update Manger', I check the 
* Canonical-supported Open Source
* Community-maintainted Open Soruce

But when I click 'Close' I get the following error 
And I see the following GPG error.  

Can you please tell me how can I fix it?

Thank you.

```


W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://archive.canonical.com natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com natty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: http://us.archive.ubuntu.com natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com natty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by lindsay7 on 2011-05-14
Do the following for the keys that you need, 
NO_PUBKEY A040830F7FAC5991 and NO_PUBKEY 40976EAF437D05B5
, see the example.  Run these in the terminal.

Code:
    gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -
When you get an error message, replace the word "KEY" with the numbers in the eror message. For your error you would enter this command 
Code:
 gpg --keyserver subkeys.pgp.net --recv F120156012B83718
After you press enter and it sends the command, you would enter the second line
Code:
 gpg --export --armor F120156012B83718 | sudo apt-key add -


then type in the folling

sudo apt-get update

and 
 

sudo apt-get upgrade

---

### Post by yinglcs2 on 2011-05-14
Thanks.
But when I tried the commands, I get this:

```

$ gpg --keyserver subkeys.pgp.net --recv 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


$ gpg --keyserver subkeys.pgp.net --recv A040830F7FAC5991
gpg: requesting key 7FAC5991 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


```

---

### Post by lindsay7 on 2011-05-14
try this, just use the last 8 digits of the key,

Code:
gpg --keyserver keyserver.ubuntu.com --recv 437D05B5
gpg --export --armor 437D05B5 | sudo apt-key add -
then run
Code:
sudo apt-get update

---


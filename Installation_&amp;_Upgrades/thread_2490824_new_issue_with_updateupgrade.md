---
title: "new issue with update/upgrade"
date: 2023-09-17
forum: Installation &amp; Upgrades
---

### Post by coley9225 on 2023-09-17
Good morning all. I'm using lubuntu 22.04, and keep it updated. I run apt update and apt upgrade once or twice a week. I have vscodium install for quite a while now.

This morning, I ran sudo apt update, and got the following err:

```

Err:7 https://download.vscodium.com/debs vscodium InRelease  Certificate verification failed: The certificate is NOT trusted. The name in the certificate does not match the expected.  Could not handshake: Error in the certificate verification. [IP: 195.181.163.202 443]

```

What may have caused this error, and more importantly, how do I fix?

Any help would be greatly appreciated.

---

### Post by MAFoElffen on 2023-09-17
I went to the IP address, and FDQN in the error, and the server that repo is on "is down", and unreachable.

Maybe you should try to contact them at: [https://github.com/VSCodium/vscodium/discussions](https://github.com/VSCodium/vscodium/discussions) and let them know there is a problem(?)

---

### Post by coley9225 on 2023-09-17
Thanks. I'll give it little time, and try again and see if the servers are up yet. If I still get the error, I'll reach out to them.

---

### Post by coley9225 on 2023-09-18
Update: After the issues yesterday, I ran sudo apt update and upgrade this morning, and it worked with no issues. Apparently, this was a temporary issue and has been resolve.

Thanks again for the help. I will go up and mark this as solved.

---


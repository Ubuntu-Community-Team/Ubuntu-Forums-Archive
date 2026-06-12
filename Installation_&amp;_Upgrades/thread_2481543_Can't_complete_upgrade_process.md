---
title: "Can't complete upgrade process"
date: 2022-12-02
forum: Installation &amp; Upgrades
---

### Post by Jason_Gauthier on 2022-12-02
Trying to upgrade from Focal to Jammy  (Both LTS)
After running  ```
sudo  do-release-upgrade  -d
```
I receive this error:

```
Checking for a new Ubuntu release
Failed to connect to https://changelogs.ubuntu.com/meta-release-lts-development. Check your Internet connection or proxy settings
There is no development version of an LTS available.
To upgrade to the latest non-LTS development release
set Prompt=normal in /etc/update-manager/release-upgrades.

```
I used lynx and wget to see if I can get to [https://changelogs.ubuntu.com/meta-release-lts-development](https://changelogs.ubuntu.com/meta-release-lts-development), and I can. But it has an outdated certificate?
```
SSL error:The certificate is NOT trusted. The certificate chain uses not yet valid certificate. -Continue? (n)

```

My thought is to update the certificates, but I can't seem to figure out how.
(update-ca-certificates was not the answer)

How can I proceed?

---

### Post by Dennis N on 2022-12-02
Try without the -d option and it should work.

---

### Post by Jason_Gauthier on 2022-12-02
It doesn't solve the certificate error.  That's the error I want to solve.

---

### Post by ian-weisser on 2022-12-02
The certificate of that site is currently valid 10 Oct 2022 to 08 Jan 2023.

Try clearing your cache.

---

### Post by Jason_Gauthier on 2022-12-02
I tried 
[COLOR=#000000][FONT=Monaco]sudo update-[/FONT][/COLOR][COLOR=#000000][FONT=Monaco]ca[/FONT][/COLOR][COLOR=#666600][FONT=Monaco]-[/FONT][/COLOR][COLOR=#000000][FONT=Monaco]certificates [/FONT][/COLOR][COLOR=#000000][FONT=Monaco]but it didn't work[/FONT][/COLOR][COLOR=#000000][FONT=Monaco]
[/FONT][/COLOR][COLOR=#000000][FONT=Monaco]However ```
sudo update[COLOR=#666600]-[/COLOR]ca[COLOR=#666600]-[/COLOR]certificates [COLOR=#666600]--[/COLOR]fresh
``` did.
Thanks!
  [/FONT][/COLOR]

---


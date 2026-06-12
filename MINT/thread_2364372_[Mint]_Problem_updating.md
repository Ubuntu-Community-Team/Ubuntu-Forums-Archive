---
title: "[Mint] Problem updating"
date: 2017-06-22
forum: MINT
---

### Post by maassen on 2017-06-22
Hi,

After updating I am getting an error message. I have looked up some possible solutions, however I am quite a noob te linux and would like to get advice on how to properly fix this issue.

```
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/additional-repositories.list:2 and /etc/apt/sources.list.d/additional-repositories.list:3
```
```

$ cat /etc/apt/sources.list
#deb cdrom:[Linux Mint 18.1 _Serena_ - Release amd64 20161213]/ xenial contrib main non-free
```

Any advice would be greatly appreciated!

---

### Post by deadflowr on 2017-06-22
*Thread moved to **MINT**.*

---

### Post by Dennis N on 2017-06-22
My advice: I would look at the given lists (additional-repositories.list:2 and additional-repositories.list:3) with a text editor for the duplicate entries, and comment out (put a # at start of entry line) or remove duplicate. You will need root permission to save changes to the files.

/etc/apt/sources.list is not being used. Repository lists are inside /etc/apt/sources.list.d. I have only one list:

```
dmn@Sydney /etc/apt/sources.list.d $ ls
official-package-repositories.list

```
The other lists named in the warning I would think are for other added repositories or ppas?

Note: The W code (W: Target Packages) is a Warning.

---

### Post by maassen on 2017-06-22
```
cat official-package-repositories.list 
deb http://packages.linuxmint.com serena main upstream import backport 

deb http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ xenial partner
```
```

cat additional-repositories.list 
deb https://cli-assets.heroku.com/branches/stable/apt ./
deb http://archive.canonical.com/ serena partner
deb http://archive.canonical.com/ serena partner
```

Should I commend the last line in additional-repositories list? Since this one is a duplicate. Also in official I see duplicates but those have different info behind the url.

EDIT: Commenting fixed this issue. Thanks for your advice!

EDIT: Is this message a problem? I got this after trying to refresh the update manager.
```

The repository 'http://archive.canonical.com serena Release' does not have a Release file.Data from such a repository can't be authenticated and is therefore potentially dangerous to use.See apt-secure(8) manpage for repository creation and user configuration details.GPG error: https://repo.skype.com/deb stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3The repository 'https://repo.skype.com/deb stable InRelease' is not signed.Data from such a repository can't be authenticated and is therefore potentially dangerous to use.See apt-secure(8) manpage for repository creation and user configuration details.Failed to fetch http://archive.canonical.com/dists/serena/partner/binary-amd64/Packages  404  Not Found [IP: 91.189.92.191 80]Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Dennis N on 2017-06-22
> EDIT: Is this message a problem? I got this after trying to refresh the update manager.

You are missing a key that is needed to verify the repository. See this for info on how to get it:

[https://askubuntu.com/questions/127326/how-to-fix-missing-gpg-keys](https://askubuntu.com/questions/127326/how-to-fix-missing-gpg-keys)

---

### Post by maassen on 2017-06-22
Thanks that worked! I feel a bit more comfortable now about fixing issues!

---


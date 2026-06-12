---
title: "Quick question about UID"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by sideburns on 2011-10-18
My sister had Ubuntu 10.10.  After a hard disk failure, we're going to install 11.11 because she might as well have the Latest and Greatest.  Before things went completely pear-shaped, I made a tarball of her home folder using sudo, to preserve file permissions, owner and so on and ftp'd it to another computer.  She was the only user on that computer and will be the only user on the new installation, with the same username.  Just to be safe, I'd like to make sure that the UID/GID will be the same as it was.

---

### Post by d.atanasov on 2011-10-18
Well google say that if you use the option "-p" of "tar" it will save the UID and all other things.

---

### Post by sideburns on 2011-10-18
Yes, I know.  I learned that from the man page.  I also learned that that, and several other things I liked were the default when done by the superuser, which is why I used sudo.  Alas, that doesn't answer my question: will her UID/GID be the same in 11.10 as it was before if she's the first (and only) user?

---

### Post by dargaud on 2011-10-18
AAfter you restore her account (as root), you can change the UID in the /etc/passwd/group files, or you can do the opposite and change the UID of all her newly restored files with:
```
find -uid 1234 -exec chown newusername:newgroupname {} \;
```

---

### Post by sideburns on 2011-10-18
Wouldn't it be easier just to answer the question I asked than to tell me what to do if the answer is "No?"

---

### Post by d.atanasov on 2011-10-18
> **sideburns said:**
> Yes, I know.  I learned that from the man page.  I also learned that that, and several other things I liked were the default when done by the superuser, which is why I used sudo.  Alas, that doesn't answer my question: will her UID/GID be the same in 11.10 as it was before if she's the first (and only) user?

Well I think it will restore all her permissions and profile after extracting the tarball to the new system. 
But what I can ask you do you think that all UUID will be the same ? I`m trying to backup and restore the hole Ubuntu and this include all the permissions of the users. This will help me understand better the process of untar the Ubuntu.

---

### Post by dave01945 on 2011-10-18
if she was the first and only user her uid should be 1000 same on a new install that's how it has always worked for me the only way to know for sure is to install and find out. if it is different in the new install just change it as dargaud suggested

---

### Post by sideburns on 2011-10-18
If I knew the answer to your question, d.atanasov, I wouldn't be asking here, because it's exactly what I'm trying to find out.

Thank you, dave01945.  That's exactly what I needed to know.  I ask because I use Fedora.  Up through Fedora 15, it always started UIDs at 500, but new installs of F 16 will start at 1000, to be consistent with other distros.  I'm only here because I'm my sister's tech support and she uses Ubuntu.

---


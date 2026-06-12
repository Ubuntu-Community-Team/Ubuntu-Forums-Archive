---
title: "SSH agent tray icon missing after upgrade to Gutsy"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by tim71 on 2007-11-14
I was trying to search the forums about this issue for many days now and ended up with nothing. So I just ended up posting here.

The problem is in SSH agent behaviour - in Feisty (and also Edgy, if I recall correctly) issuing 
```
ssh-add
```
opened the box asking passphrase for my id_rsa private key. After entering the correct passphrase the box disappeared and icon appeared in notification area. This icon gave the possibility for accesing the ssh-agent settings AND clear the passphrase cache with two clicks, which was very convenient to use when all ssh connections were closed and job was done. This was also a good way to indicate whether the private key is "active" - exactly like Pageant in Windows environment.

Now everything appeares to be almost the same - with this little annoying difference that this icon is not appearing anymore and there is no convenient way to do these actions like before - and there is no visual indication about the ssh agent state.

I don't know if this is some kind of bug, upgrade issue or intentional change of behaviour.

Has anyone got an idea, what this might be about?

At least I am not happy with this issue :confused:

---

### Post by tim71 on 2007-12-14
Obviously either noone has faced the same problem or has not seen this thing as a problem - but now I found a solution.

Open gconf-editor and go to /apps/seahorse/agent and activate the 'cache_display' option - and all is fine again. :)

---

### Post by zivagolee on 2007-12-31
Wow!  I've been trying to find a solution to this and I finally came across your post!

THANKS!!!

---

### Post by tim71 on 2008-06-11
> **zivagolee said:**
> Wow!  I've been trying to find a solution to this and I finally came across your post!

THANKS!!!

Good to know, that it helped somebody, but... now after upgrade to Hardy the problem is back and this trick does not work anymore :confused:

---

### Post by zivagolee on 2008-06-11
> **tim71 said:**
> Good to know, that it helped somebody, but... now after upgrade to Hardy the problem is back and this trick does not work anymore :confused:

Yea, same here.  GPG agent works fine and I get a key icon for that but not for the SSH agent.

---


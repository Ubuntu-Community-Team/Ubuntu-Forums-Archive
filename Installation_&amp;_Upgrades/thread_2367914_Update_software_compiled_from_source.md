---
title: "Update software compiled from source"
date: 2017-08-04
forum: Installation &amp; Upgrades
---

### Post by ty89 on 2017-08-04
Hi.

I know you have to recompile or use git to update software compiled from source, but what happens to the config files etc.? Do we have to configure and set everything up from scratch?

Thanks,

Ty

---

### Post by vocx on 2017-08-04
> **ty89 said:**
> Hi.

I know you have to recompile or use git to update software compiled from source, but what happens to the config files etc.? Do we have to configure and set everything up from scratch?

Thanks,

Ty
I'm sorry but your question is too vague. What program compiled from source? What "config files etc."? What needs to be "configured" and "set up from scratch"?

Truth is, different programs are installed in different ways. Some are extremely simple, and you basically just compile, move the binary file to a place, and then you are ready to go. Others, well it really depends, what the programs do, what files they read, what other dependencies they have, etc.

So, yes, if a program needs configuration files, it could use existing ones, or provide new ones.

You see. There is essentially no way to answer your question in a general way, because there are many different kinds of programs and they all behave differently. So, if you want a better response, you need to ask a more defined question.

---

### Post by ty89 on 2017-08-04
I'm sorry for the vague question. I want to set up samba.

Thanks for the answer btw.

---

### Post by vocx on 2017-08-04
> **ty89 said:**
> I'm sorry for the vague question. I want to set up samba.

Thanks for the answer btw.
If you want to install samba, you don't need to compile it yourself as it is readily available from the Ubuntu repositories.

[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)

Just install it and configure the options in its files and that should be it. If something doesn't work, then you may come back to the forums and really ask a specific question: "I tried installing samba using this guide, and I gave the workspace name and this options, but it did not connect, what did I do wrong?", for example.

If for some reason you really want to compile and install samba from source, then I would ask you to gain much more experience with compiling and installing software from source, because otherwise you will get frustrated with a ton of errors. If you want to install samba, follow the guide above and worry about compilation another time.

---

### Post by ty89 on 2017-08-05
The reason i wanted to compile from source was that i then could get the latest update faster. But i'm not sure that i need it. I will for now just install it as usual :)

---

### Post by monkeybrain20122 on 2017-08-05
The config files should not be affected.

---

### Post by vocx on 2017-08-05
> **ty89 said:**
> The reason i wanted to compile from source was that i then could get the latest update faster. But i'm not sure that i need it. I will for now just install it as usual :)
Correct. You don't need the latest of the latest just for the sake of it.

If you are getting software from source and compiling it yourself it's because you absolutely must have a specific function that is not available in the version of the repositories. For your case, your are better just getting the regular version installed with "apt".

---


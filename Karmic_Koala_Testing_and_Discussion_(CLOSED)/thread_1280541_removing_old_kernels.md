---
title: "removing old kernels"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-10-02
i used this method prior to 9.10. first typed uname -r in terminal to identify the most current one then went to spm and typed in linux-image-2 in the search box and this identified all the older kernels and deleted them. doesnt seems to work any more and ideas

---

### Post by dino99 on 2009-10-02
spm ?

---

### Post by wojox on 2009-10-02
Karmic doesn't have Computer Janitor?

---

### Post by dino99 on 2009-10-02
> **wojox said:**
> Karmic doesn't have Computer Janitor?

yes it have

---

### Post by dino99 on 2009-10-02
> **rburkartjo said:**
> i used this method prior to 9.10. first typed uname -r in terminal to identify the most current one then went to spm and typed in linux-image-2 in the search box and this identified all the older kernels and deleted them. doesnt seems to work any more and ideas

look at /lib/modules

& rm -f those you don't need

---

### Post by forumache on 2009-10-02
> **rburkartjo said:**
> doesnt seems to work any more and ideas

"does not work" is non-descriptive.


Please explain what happens: error messages, old kernels not found, or what?

---

### Post by slakkie on 2009-10-02
```

rmkernel () {
        local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
        local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
        local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
        sudo aptitude purge $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
}

```

---

### Post by wojox on 2009-10-02
> **slakkie said:**
> ```

rmkernel () {
        local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
        local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
        local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
        sudo aptitude purge $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
}

```

I knew you'd be in here soon pimpin your script :lolflag:

---

### Post by slakkie on 2009-10-02
> **wojox said:**
> I knew you'd be in here soon pimpin your script :lolflag:

:) I've added another kernel since your last additions btw.

---

### Post by wojox on 2009-10-02
I know I was looking at it :P

---

### Post by rburkartjo on 2009-10-02
dino tks didnt think of using the computer janitor or looking at /lib/modules

---

### Post by jlacroix on 2009-10-02
> **slakkie said:**
> ```

rmkernel () {
        local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
        local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
        local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
        sudo aptitude purge $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
}

```

How do I use that? I ran it but nothing happened. :(

---

### Post by forumache on 2009-10-02
> **jlacroix said:**
> How do I use that? I ran it but nothing happened. :(

Something happened: you defined the rmkernel function.

Now type rmkernel in the same terminal and it will be executed.

Add the definition to one of the shell configuration files to be available in the future (you don't want to type it every time)

---

### Post by jlacroix on 2009-10-02
> **forumache said:**
> Something happened: you defined the rmkernel function.

Now type rmkernel in the same terminal and it will be executed.

Add the definition to one of the shell configuration files to be available in the future (you don't want to type it every time)

I just copied the code into a shell script. I added the rmkernel to the end of the script and that worked. Thank you!

Now one thing that is *really* weird is that when I do "ls" on /lib/modules, I see entries for 2.6.27-14 and 2.6.27-14-server. This was a clean install of Kubuntu Karmic, I wonder why I'd have those?!

Edit: Nevermind, Virtualbox must have created those for some reason because that's the only modules listed in there for those.

---

### Post by johnnybirdman on 2009-10-28
> **slakkie said:**
> ```

rmkernel () {
        local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
        local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
        local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
        sudo aptitude purge $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
}

```
Thanks for this, works great.
J.

---


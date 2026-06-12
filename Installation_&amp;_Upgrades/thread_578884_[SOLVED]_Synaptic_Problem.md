---
title: "[SOLVED] Synaptic Problem"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by Dave Otter on 2007-10-17
WEhen I attempt to use Synaptic I get an error message-E: dpkg was interrupted, you must manually run 'dpkg --configu re -a' tocorrect the problem. 
      How do I do that?
                      Thanks

---

### Post by Pumalite on 2007-10-17
At the Terminal:
sudo dpkg --configure -a
Post back if you keep having problems.

---

### Post by troy1of2 on 2007-10-17
> **Dave Otter said:**
> WEhen I attempt to use Synaptic I get an error message-E: dpkg was interrupted, you must manually run 'dpkg --configu re -a' tocorrect the problem. 
      How do I do that?
                      Thanks

Applications>Accessories>Terminal
```

sudo dpkg --configure -a
```

Type in your password when prompted and it'll do the rest...

---

### Post by Dave Otter on 2007-10-17
Still having problem-I did as u suggested and dpkg came up and asked if I wanted to install F Prot installer,This appears to be the package that caused the problem

---

### Post by Pumalite on 2007-10-17
Post the entire output of the error to see if we can help you. Most probably you need to force remove the package and then reinstall.

---

### Post by Dave Otter on 2007-10-19
Many thanks to Troy and Pumalite.
    Your instuructions worked but I was too impatient to await result!

                          Many thanks

---

### Post by hammad1337 on 2008-02-21
a partially installed package caused the same problem in my pc.
I donot want to install the package anymore, can you tell me how to force remove it?

---

### Post by Pumalite on 2008-02-21
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by hammad1337 on 2008-02-21
Thanks :)

---

### Post by Pumalite on 2008-02-21
You are welcome. Good luck.

---


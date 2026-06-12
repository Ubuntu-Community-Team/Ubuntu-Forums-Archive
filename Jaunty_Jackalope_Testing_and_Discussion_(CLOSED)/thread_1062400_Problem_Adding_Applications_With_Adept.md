---
title: "Problem Adding Applications With Adept"
date: 2009-02-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2009-02-06
After installing Alpha 4, I added the Medibuntu repository and GPG key.  Likewise, I checked all the usual boxes for update in Sources.  

I've never encountered this issue before, but when I attempt to install MPlayer or several other packages, most of which I think are from Medibuntu, I get the following error.

Download failed.
The list of errors is attached. The recovery for this case is currently not implemented. If you see 404 errors, it might be useful to try fetching package lists (see the Sources tab) and retrying the operation.

The error was: 
APT Error. Context:
    Package download failed, 
    Unable to correct problems, you have held broken packages., 
    : , 
    : , 
    : , 
    : , 
    : , 
    : , 
    

I have refreshed the sources and done everything I know of, so I'm wondering if it's some problem I have, or if anyone else is also experiencing this.

Any help would be appreciated.

Thanks,
zenarcher

---

### Post by tarahmarie on 2009-03-30
Ditto and bump

---

### Post by cariboo on 2009-03-30
You have broken packages, nothing is going to happen until you fix them. Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages, and correct the errors.

You could also try:

```
sudo apt-get install -f
```

then

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Jim

---


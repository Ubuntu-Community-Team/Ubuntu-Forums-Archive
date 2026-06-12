---
title: "medibuntu for intrepid"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by doubad on 2008-10-16
likely a newb question here BUT I keep getting this message
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
I've never had problems putting in a medibuntu repo before, am i doing something wrong?

---

### Post by jblackhall on 2008-10-16
Have you added the GPG key correctly after adding the repo?  I haven't tried Medibuntu yet since upgrading, so I'm not sure if it's something broken or not.

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by warjowuch on 2008-10-16
I guess it is not normal for 3rd party repositories to "exist" before the official release is out.
I have seen this before on other 3rd party repos, and they act normal a few days (or the same day) when it is officially released.

Oh, while I just see on their page a refereence to de medibuntu intrepid repo. Hmm. Then it's just weird (try the suggestion from the 2nd post), or they are way too fast to show it on the webpage while it isn't up yet. :S

---

### Post by OrangeCrate on 2008-10-16
> **doubad said:**
> likely a newb question here BUT I keep getting this message

I've never had problems putting in a medibuntu repo before, am i doing something wrong?

It's working fine here. Just reinstall the intrepid repo, and the key. They can be found here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---


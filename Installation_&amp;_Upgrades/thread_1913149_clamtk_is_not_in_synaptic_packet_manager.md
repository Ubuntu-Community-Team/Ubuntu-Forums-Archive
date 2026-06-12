---
title: "clamtk is not in synaptic packet manager"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by Terry@nz on 2012-01-22
I have ubuntu 10.4 LTS on a flash drive.
I am new to Ubuntu, still struggling, but have been with Windows for years; command lines are no problems to me but I prefer GUIs.

I keep seeing that clamtk should be in the synaptic package manager but it is not there. The other clam packages are there and installed.

I have tried other sites that tell me how to install clamtk in the terminal but it has never worked for me.

Anyone help?

Terry

---

### Post by raja.genupula on 2012-01-22
have you tried clamtk in software center , because i am also using 10.04 LTS and that was in .

i am attaching Image to give you an idea about that.
All the best.

---

### Post by spcwingo on 2012-01-22
> **Terry@nz said:**
> I have ubuntu 10.4 LTS on a flash drive.
I am new to Ubuntu, still struggling, but have been with Windows for years; command lines are no problems to me but I prefer GUIs.

I keep seeing that clamtk should be in the synaptic package manager but it is not there. The other clam packages are there and installed.

I have tried other sites that tell me how to install clamtk in the terminal but it has never worked for me.

Anyone help?

Terry

If you're running Lucid from a flash as non-persistant then it will only see some of the packages in the repos (I have no idea why).  Try this command from the terminal:

```
sudo apt-get update && sudo apt-get install clamtk
```

If that doesn't work you first have to enable the universe repository.  If you need help with that, just let me know.  I will be wore than willing to give you a hand.  :)

---


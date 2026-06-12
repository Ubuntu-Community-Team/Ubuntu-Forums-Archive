---
title: "Update Error"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by KB1LQC on 2007-12-21
I just got this error when trying update manager, can anyone help?

'E:Malformed line 82 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'




Thank You,

KB1LQC

---

### Post by taurus on 2007-12-21
There is something wrong with line 82 in your /etc/apt/sources.list. So, you need to edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

and remove that line from /etc/apt/sources.list. Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

Otherwise, just post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by KB1LQC on 2007-12-21
I got up to the update portion fine and the last part of the output in terminal:

> W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7





Thank You,

KB1LQC

---

### Post by taurus on 2007-12-21
Can you post your /etc/apt/sources.list?  Looks like you have both feisty and gutsy repos in there at the same time!  

Which release are you running right now anyway?

```
cat /etc/apt/sources.list
```

---

### Post by oldsoundguy on 2007-12-21
I am also getting an update error on one machine.  (But, different than the above errors.)
I have three machines running Gutsy  7.10 and two have updated this morning without a hitch.  However, the third machine gives me a "not all updates can be installed" pop up with the option of doing a partial update.  When I hit that button and sign in, it does it's thing but up pops a screen showing that NONE of the 20 items can be updated as they can not be "authenticated".  
Would add that this machine is a newer install using the "Alternative" disk, not the live install as the live gave me a ration on the install and a lot of BIOS tweaking was required to get even the alternative  to install. (much older and slower box.)
Have the same list of repositories on all three boxes.

Asus board
PIII 733
768 running at 133
80gb hd running a 6gb primary partition
ATI 9800

Other than the updater, the machine runs fine.

---

### Post by taurus on 2007-12-21
> **oldsoundguy said:**
> I am also getting an update error on one machine.  (But, different than the above errors.)
I have three machines running Gutsy  7.10 and two have updated this morning without a hitch.  However, the third machine gives me a "not all updates can be installed" pop up with the option of doing a partial update.  When I hit that button and sign in, it does it's thing but up pops a screen showing that NONE of the 20 items can be updated as they can not be "authenticated".  
Would add that this machine is a newer install using the "Alternative" disk, not the live install as the live gave me a ration on the install and a lot of BIOS tweaking was required to get even the alternative  to install. (much older and slower box.)
Have the same list of repositories on all three boxes.

Asus board
PIII 733
768 running at 133
80gb hd running a 6gb primary partition
ATI 9800

Other than the updater, the machine runs fine.

What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by oldsoundguy on 2007-12-21
first tells me I have dupication of sources ... that I can fix (I think)

the update incon indicated 20 updates .. howsmever there ... 
the second command line did a get on 29 packages and unpacked and replaced and did the setup on ALL of them!

Thanks a bunch for the code!

---


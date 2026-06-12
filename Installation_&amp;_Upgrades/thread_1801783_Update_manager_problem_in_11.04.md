---
title: "Update manager problem in 11.04"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by pranav.33 on 2011-07-11
When i open my update manager i get this error in my newly installed 11.04. 

'E:Encountered a section with no Package: header, E: problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened

Also the software centre and synaptic package manager doesn't work :(

Can i get help?

---

### Post by M.Sisco on 2011-07-11
I'm having the exact same error message. Anyone know a solution?

---

### Post by raja.genupula on 2011-07-11
well guys i have the solution for you 

 do this 

           sudo rm -rf /var/lib/apt/lists/*
            
and the run update 
          
           sudo apt-get update

---

### Post by pranav.33 on 2011-07-11
That worked thanks =) Btw I have 10.10 Ubuntu installed in my laptop. I'm not able to connect it to the net through Ethernet cable. It says device not managed. Any help on that?

---

### Post by tlue on 2011-07-11
> **raja.genupula said:**
> well guys i have the solution for you 

 do this 

           sudo rm -rf /var/lib/apt/lists/*
            
and the run update 
          
           sudo apt-get update

Thanks a lot:), that helped me too.

---


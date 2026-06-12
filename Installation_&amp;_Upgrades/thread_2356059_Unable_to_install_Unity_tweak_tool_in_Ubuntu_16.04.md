---
title: "Unable to install Unity tweak tool in Ubuntu 16.04?"
date: 2017-03-19
forum: Installation &amp; Upgrades
---

### Post by maxyspark on 2017-03-19
I had Installed "Unity Tweak Tool". But now it disappeared.


When I tried to install again it shows the following output  
```
sudo apt-get install unity-tweak-tool
```


    ```
Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Some packages could not be installed. This may mean that you have
    requested an impossible situation or if you are using the unstable
    distribution that some required packages have not yet been created
    or been moved out of Incoming.
    The following information may help to resolve the situation:
    
    The following packages have unmet dependencies:
     unity-tweak-tool : Depends: unity-webapps-common but it is not going to be installed
    E: Unable to correct problems, you have held broken packages.

```



Screenshot -

[IMG]https://i.stack.imgur.com/tkDzn.png[/IMG]

---

### Post by luckie2 on 2017-03-26
I am having the same issue.  Were you able to find a solution?

---

### Post by Perfect Storm on 2017-03-26
Try install unity-webapps-common first

```
sudo apt install unity-webapps-common
```

---

### Post by luckie2 on 2017-03-26
That seems to just lead to another package that wont install.   Then when trying to install that package, it throws another 
package that wont install. (see below) I went about 7 dependencies deep and it does the came thing every time. 

Also this seems to be the only package that has problems installing.  Everything else i have installed is working fine. 
---------------------------------------------------
sudo apt install unity-webapps-common
[sudo] password for ********: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-webapps-common : Depends: unity-webapps-service (>= 2.3.8-0ubuntu3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

 sudo apt install unity-webapps-service
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-webapps-service : Depends: webapp-container
E: Unable to correct problems, you have held broken packages.

---

### Post by Perfect Storm on 2017-03-26
Let's try this way:

```
sudo apt -f install
```

---

### Post by MilkThief on 2017-04-27
Same issue, no working solution found...

---

### Post by Frogs Hair on 2017-04-27
Make sure the Canonical Partners repository is enabled in Software & Updates under other software. Then try the following and if there are no errors try and install again.

```
sudo apt update
``` ```
 sudo dpkg --configure -a 

```

---


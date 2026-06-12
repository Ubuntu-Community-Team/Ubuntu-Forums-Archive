---
title: "running script with super user rights?"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by bl42ed0 on 2011-04-10
im trying to get vmware installed by using this [documentation]("https://help.ubuntu.com/community/VMware/Server").

i already have both the vmware file and the script file downloaded in the same folder. how do i run the script in terminal?

---

### Post by mikewhatever on 2011-04-10
```

cd folder-name

sudo ./script-name

```

... sudo makes it run with as super user.

---

### Post by spcwingo on 2011-04-10
Just put sudo in front of the command (script in this case).  So, let's say that you have the script in your home directory.  Cd to that directory like this:

```
cd ~
```

or ```
cd /home/your_user_name
```

Then run the script like this:

```
sudo ./script_name
```

That should fix ya up!  ;)

---

### Post by bl42ed0 on 2011-04-10
> **spcwingo said:**
> Just put sudo in front of the command (script in this case).  So, let's say that you have the script in your home directory.  Cd to that directory like this:

```
cd ~
```

or ```
cd /home/your_user_name
```

Then run the script like this:

```
sudo ./script_name
```

That should fix ya up!  ;)

thanks for the help but after i tried running the script it gave me a "command not found". i copied and pasted the script so that shouldnt be a problem? its a tar.gz file.

---

### Post by mikewhatever on 2011-04-10
Tar.gz is an archive, not a script. Try unpacking it (right click, 'Extract here'), and then
```
cd raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66

sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
```

---

### Post by bl42ed0 on 2011-04-10
> **mikewhatever said:**
> Tar.gz is an archive, not a script. Try unpacking it (right click, 'Extract here'), and then
```
cd raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66

sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
```

sorry..i must be retarded. now its telling me there is no archive containing vmware server found no matter where i put the vmware folder extracted or not...

---

### Post by spcwingo on 2011-04-10
This is taken directly from the readme file included in the script that is referred to [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/VMware/Server") and downloaded from [[COLOR="Red"]here[/COLOR]]("http://codebin.cotescu.com/vmware/vmware-server-2.0.x-kernel-2.6.3x-install.sh"):

> Example on how to run the script:

    chmod +x vmware-server-2.0.x-kernel-2.6.3x-install.sh
    sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh [PATH _TO_VMWARE_ARCHIVE]

---

### Post by Crusty Old Fart on 2011-04-10
There's a much safer way to do it in [post=10317361]This post[/post].

Ooops...sorry...wrong thread. Probably way more information than you wanted.

---

### Post by mikewhatever on 2011-04-10
> **bl42ed0 said:**
> sorry..i must be retarded. now its telling me there is no archive containing vmware server found no matter where i put the vmware folder extracted or not...

Don't extract the VMware archive because the installation script will be looking for it. If you don't specify the path, it will be looking in the same directory from where you run the installation script.

---

### Post by bl42ed0 on 2011-04-10
okay now that i have it installed where do i find the program to run it? its not located under applications.

---

### Post by spcwingo on 2011-04-10
I believe it has a webUI.  To access it open your browser and enter either of these addresses:

> [http://localhost:8222/](http://localhost:8222/)

or

> [https://localhost:8333/](https://localhost:8333/)

---


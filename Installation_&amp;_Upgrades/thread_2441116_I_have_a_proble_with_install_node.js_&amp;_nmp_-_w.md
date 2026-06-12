---
title: "I have a proble with install node.js &amp; nmp - who can help ?"
date: 2020-04-19
forum: Installation &amp; Upgrades
---

### Post by getting-power-or-powder on 2020-04-19
I have used this commands and have errors, i don't know what to do... 
```

[LIST]
[*]curl -sL https://deb.nodesource.com/setup_10.x -o nodesource_setup.sh 
[/LIST]

``` 
You can inspect the contents of this script with nano (or your preferred text editor):
```


 
[LIST]
[*]nano nodesource_setup.sh 
``` 
[/LIST]
 Run the script under sudo:
```
  
[LIST]
[*]sudo bash nodesource_setup.sh 
``` 
[/LIST]
 The PPA will be added to your configuration and your local package  cache will be updated automatically. After running the setup script from  Nodesource, you can install the Node.js package in the same way you did  above:
```
  
[LIST]
[*]sudo apt install nodejs 
``` 
[/LIST]


How to fix this problem? 

 ```

use@closect:~$ sudo apt-get install nodejs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nodejs : Depends: python-minimal but it is not installable
E: Unable to correct problems, you have held broken packages.

```

---

### Post by TheFu on 2020-04-19
Do you trust nodesource.com?  Running a random script from a random site is dangerous.  Running a random script from a random site as root (w/ sudo) is asking to give your machine to them.

I don't know anything about nodesource.

The script looks like it adds a few PPA keys and sources, so they will be able to install/update the software from that PPA later.  Hopefully, they are trustworthy.
[https://security.stackexchange.com/questions/213401/is-curl-something-sudo-bash-a-reasonably-safe-installation-method/213420](https://security.stackexchange.com/questions/213401/is-curl-something-sudo-bash-a-reasonably-safe-installation-method/213420)

I don't use node.js for anything.  If I were going to help troubleshoot this, I'd need the specific release you are running.  Something like *Ubuntu 16.04.6 LTS* which is from the **lsb_release -a** command.

Also, you should manually perform your weekly patching before looking for help with package management:  [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) - updated for 2020.

---

### Post by getting-power-or-powder on 2020-04-19
> Do you trust nodesource.com? 

I am trying, because i need this.
> I don't know anything about nodesource.
I am too.

> [https://security.stackexchange.com/questions/213401/is-curl-something-sudo-bash-a-reasonably-safe-installation-method/213420](https://security.stackexchange.com/questions/213401/is-curl-something-sudo-bash-a-reasonably-safe-installation-method/213420)
I have tryed again, but it's again.
 > **lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

---

### Post by kostkon on 2020-04-19
A better way to achieve what you want would be to use [nvm]("https://github.com/nvm-sh/nvm").

---

### Post by getting-power-or-powder on 2020-04-19
Thank you, i have installed> **kostkon said:**
>  like you  recommend and like here  > [https://stackoverflow.com/questions/54542402/how-to-install-node-js-in-ubuntu-18-10](https://stackoverflow.com/questions/54542402/how-to-install-node-js-in-ubuntu-18-10) but it is not help to me decide the problem with python-minimal package... i an looking for other themes but can't found answer who has decided this problem

:~$ nvm ls
->          v4.4.5  
->     v13.13.0  
default -> node (-> v13.13.0)
node -> stable (-> v13.13.0) (default)
stable -> 13.13 (-> v13.13.0) (default)
iojs -> N/A (default)
lts/* -> lts/argon (-> N/A)
lts/argon -> v4.9.1 (-> N/A)
lts/boron -> v6.17.1 (-> N/A)
lts/carbon -> v8.17.0 (-> N/A)
lts/dubnium -> v10.20.0 (-> N/A)
lts/erbium -> v12.16.2 (-> N/A)


than typed: npm -v press ENTER and get version of npm:

6.14.4

than typed: nodejs -v

Command 'nodejs' not found, but can be installed with:

sudo apt install nodejs

---

### Post by getting-power-or-powder on 2020-04-19
I did it! [https://askubuntu.com/questions/1222566/not-able-to-install-nodejs-in-ubuntu-command-line](https://askubuntu.com/questions/1222566/not-able-to-install-nodejs-in-ubuntu-command-line)

nodejs -v
v13.13.0

---


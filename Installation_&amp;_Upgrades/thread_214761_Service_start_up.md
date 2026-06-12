---
title: "Service start up"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by Danielito on 2006-07-13
Hello.

Recently I have realized that when restarting the computer, most of the services such as apache2, mysql, ssh, nfs, powernow don't start.:o I have to start them manually in order to work.

I have been having a look into rcX.d directories and there are links called SXServiceName pointing to /etc/init.d/service. I have tried to configure the start up of such services with BUM. Still I don't know why the don't start.:confused: 

I have seen the /etc/inittab file and the default level is level 2. I wonder if this means that I have to put all the services I want to start when booting in rc2.d. I have also tried to change the default level to 5, but things were worse. I got some errors like something with the voltage scaling of the processor, like if  powernowd didn't like the change.:confused: 

If I haven't touch anything concerning init levels, nor init scripts, why suddenly it stops working?:( 

Another problem I have found, I don't know if concerning this issue, is related to terminals. I can't switch to tty1-tty6, I only get blank screens. I wonder if there is a service start up missing.

Can anyone help me?
Could it be due to a software upgrade?

I am using dapper, but began installing dapper pre-version 7.

Thanks

---

### Post by Danielito on 2006-07-17
Hi,

I have found the reason for this behaviour. When adding amuled to init scripts a link in rc2.d, rc3.d, rc4.d and rc5.d appears in S20amuled. The scripts which are to be launched behind this one are not executed. I have tried to rename it to S97amuled and all the scripts before it where executed properly. I Don't know why. I have ommited amuled until I know what is happening. Probably the script for amuled I got is wrong. I got it from amule wiki.

Has anyone seen this before?

Cheers

---


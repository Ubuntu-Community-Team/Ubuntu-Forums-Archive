---
title: "New printer -   brother MFC-L2700dW install on ubuntu"
date: 2022-04-11
forum: Installation &amp; Upgrades
---

### Post by dokbrown2 on 2022-04-11
New printer - brother MFC-L2700dW install on ubuntu

[https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfcl2700dw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625]("https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfcl2700dw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625")

printer:
MFC-L2700dW

package:
linux-brprinter-installer-2.2.3-1

I&#8217;ve been running the following command to no avail


```
sudo bash linux-brprinter-installer-2.2.3-1 MFC-L27000dW
```


Step4. Enter this command to extract the downloaded file

Command: gunzip linux-brprinter-installer-*.*.*-*.gz
e.g. gunzip linux-brprinter-installer-2.1.1-1.gz


Step5. Get superuser authorization with the "su" command or "sudo su" command.


Step6. Run the tool:

Command: bash linux-brprinter-installer-*.*.*-* Brother machine name
e.g. bash linux-brprinter-installer-2.1.1-1 MFC-J880DW

---

### Post by ActionParsnip on 2022-04-12
Don't you extract the archive, then inside there are debs and even an install.sh file to run?

---

### Post by dokbrown2 on 2022-04-12
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_PROBLEM SOLVED_[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_OLD COMMAND_[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_sudo bash linux-brprinter-installer-2.2.3-1 MFC-L27000dW_[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_FIXED COMMAND_[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_sudo bash linux-brprinter-installer-2.2.3-1 MFC-L2700dW_[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_PROBLEM SOLVED_[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_OLD COMMAND_[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_sudo bash linux-brprinter-installer-2.2.3-1 MFC-L27000dW_[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_FIXED COMMAND_[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Dyuthi]_sudo bash linux-brprinter-installer-2.2.3-1 MFC-L2700dW_[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]

---


---
title: "Installing a Virtual Machine on 7.04"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by rabideau on 2007-04-20
***_This is a description for installing VirtualBox._***


**_VirtualBox Install_**

To install VirtualBox 1.3.8 on Feisty Fawn (7.04) of Ubuntu, simply download the ubuntu 6.10 version of VirtualBox from [www.virtualbox.org](www.virtualbox.org).

1. Once downloaded double-click on the package installer to open the install.

2. Next select "Details" button to see software dependencies that are required for VirtualBox. DO NOT click on INSTALL, yet!

3. Open Synaptic Package Manager and install the dependent modules/apps.

4. Once these have installed, go back to the VirtualBox Package Installer and click on "Install Package" . I recommend closing Synaptic Package Manager and any other open apps prior to performing the VirtualBox install (especially on slow machines like mine!)

5. Once you select Install... open the terminal box option and answer all questions.

6. After the VirtualBox was setup all I had to do was install my WinDoze software and OS.

If you need additional information, go to this webpage for more information (I did!)
[http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/](http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/)

[B][I]If you want to view a good review of VM packages that run on Linux, visit this page:
[http://www.linux-gamers.net/modules/smartsection/item.php?itemid=56](http://www.linux-gamers.net/modules/smartsection/item.php?itemid=56)
[/I][/B]
I hope this helps someone....

---

### Post by honeydew on 2007-04-20
hey thanks.. I just tried it and I breezed through it works fine thanks =].. do you know why it is nesisary to install the dependencies through synaptic first?

---

### Post by honeydew on 2007-04-20
welll it didnt go quite as planned.. I keep on getting this error.. the problem is I have added the users to the group..

> 
VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

---

### Post by rabideau on 2007-04-20
You can fix that problem through your System>>Admin>>User&Groups settings.

Like you have a problem now too...  I can't seem to share disk drives.  For some reason my machine did not register.:confused:

Try this command ~$ VBoxManage list vms before going much further to make certain your VirtualMachine is registered.

Also you will need VBoxManage commands to make things work.

---


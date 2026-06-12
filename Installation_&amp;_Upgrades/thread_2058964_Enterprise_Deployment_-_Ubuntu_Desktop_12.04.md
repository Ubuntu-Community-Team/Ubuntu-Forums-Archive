---
title: "Enterprise Deployment - Ubuntu Desktop 12.04"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by huzefa_from_kuwait on 2012-09-17
Hello people,

We just planned to move all desktops in our enterprise to Ubuntu. There are a few settings in the current MS setup which I wish to replicate it to Ubuntu as well. The one that I am currently working on, and unable to solve (and require your expert help) are:

1) To prevent normal users (sudo is restricted) from accessing any type of system or user settings (change themes, desktop etc) by hiding them. Earlier this was attained by GPO.

2) To prevent users from navigating to any other folder structure except for their home directories. (deleting all references and shortcuts from nautilus)

3) Allow USB ports (for mouse and keyboard) but disable flash drives. (A registry hack did this earlier in MS)

Thanks.

---

### Post by Mohan1289 on 2012-09-17
as for to prevent all the users from navigating t any other folder structure except their home folder i think you can do it with "chmod" by giving the directory name..

try chmod 700 / /bin /etc /bin etc... (except don't put home folder there)

here only admin can access the directories you mentioned above.. 

Correct me if i'm wrong

---

### Post by kaytrance on 2012-09-17
1. remove user group (or separate user) from sudoers
2. umm.. yeah, maybe chmod will be the right solution.
3. I think it's only possible to make USB flash drives read-only.

---

### Post by Mohan1289 on 2012-09-17
i think it's better to remove the User Group than separate the users from the group since that's an enterprise they'll have large number of user's.. I think it's better to Remove User Group and use "chmod" command

---

### Post by kaytrance on 2012-09-17
> **Mohan1289 said:**
> i think it's better to remove the User Group than separate the users from the group since that's an enterprise they'll have large number of user's.. I think it's better to Remove User Group and use "chmod" command
yes, I agree.

---

### Post by Scott Harrison on 2012-09-17
> **huzefa_from_kuwait said:**
> Hello people,

We just planned to move all desktops in our enterprise to Ubuntu. There are a few settings in the current MS setup which I wish to replicate it to Ubuntu as well. The one that I am currently working on, and unable to solve (and require your expert help) are:

1) To prevent normal users (sudo is restricted) from accessing any type of system or user settings (change themes, desktop etc) by hiding them. Earlier this was attained by GPO.

2) To prevent users from navigating to any other folder structure except for their home directories. (deleting all references and shortcuts from nautilus)

3) Allow USB ports (for mouse and keyboard) but disable flash drives. (A registry hack did this earlier in MS)

Thanks.
This sounds like a great project... I have some questions if you don't mind me asking?

Firstly, what applications will make up your SOE? For example, what email client will you use to replace Outlook?

---

### Post by huzefa_from_kuwait on 2012-09-17
First of all thanks for all the replies.

> **Mohan1289 said:**
> as for to prevent all the users from navigating t any other folder structure except their home folder i think you can do it with "chmod" by giving the directory name..

try chmod 700 / /bin /etc /bin etc... (except don't put home folder there)

here only admin can access the directories you mentioned above.. 

Correct me if i'm wrong

I practically can't do that because if I do (as I understand you) the user shall not have any access to the /bin directory at all which in case he won't be able to use any of the applications installed  (like openoffice).


> **kaytrance said:**
> 1. remove user group (or separate user) from sudoers
2. umm.. yeah, maybe chmod will be the right solution.
3. I think it's only possible to make USB flash drives read-only.

I have already removed the from sudoers yet I can't hide the "System Settings", "Displays" etc kind of stuff from the Ubuntu Unity Desktop. I don't want my users to put fancy kind of wallpapers on their desktop or some colourful mouse pointers or some fancy themes, it doesn't look professional to an arriving customer.

The company content is sensitive and I certainly need to block access to flashdrives. If there is some driver file that loads during accessing flash drives (as it was USBSTOR with MS) and if we cant restrict access to it, then it might work but I am not sure.

> **Scott Harrison said:**
> This sounds like a great project... I have some questions if you don't mind me asking?

Firstly, what applications will make up your SOE? For example, what email client will you use to replace Outlook?

We have an Oracle 3-Tier Application server so basically the client means a browser. Apart from that there is OpenOffice and Thunderbird. Currently on MS clients also we are using OpenOffice and Thunderbird so I suppose migration won't be that clumsy.

---

### Post by kaytrance on 2012-09-17
> Firstly, what applications will make up your SOE? For example, what email client will you use to replace Outlook?
The company I work at now moves to Zimbra from VMWare. The only missing thing I found (comparing to MS outlook) is unable to make reccurent tasks.

---

### Post by huzefa_from_kuwait on 2012-09-23
There is one another issue,

We have an Oracle Application server 11g 3-Tier application. This application runs on java and is run through the browser.

The application is in two languages arabic and english. The problem is when we switch the language to arabic the text comes but the orientation does not flip from LTR to RTL.

Earlier in MS this setting was controlled from the regional settings. In regional settings if we supplied Arabic (Kuwait) then it would flip fine. 

The question is how can I do the same thing in Ubuntu ?

Thanks.

---

### Post by itmltd on 2012-10-23
You can disable USB storage without actually disabling USB ports. 
Use the command below:

sudo  echo "blacklist usb-storage" >> /etc/modprobe.d/blacklist.conf

Cheers,

---


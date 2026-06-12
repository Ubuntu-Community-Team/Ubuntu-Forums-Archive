---
title: "Help me"
date: 2010-01-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aaydinalp on 2010-01-02
I have installed windows office 2007  successful when I try to run any office program like windows word or poweroffice wine says  it starting and then it gone

I don't know how to fix it
I am using ubuntu  10.04 alpha 1 and wine 1.2
please someone helps me

---

### Post by lisati on 2010-01-02
<edit>
Might be better to do as others have suggested, and use an earlier version of Ubuntu

---

### Post by wieman01 on 2010-01-02
If you are a day-to-day user, I would not recommend version 10.04 because it is still alpha. I would rather user 9.10 which will save you a lot of trouble.

---

### Post by rovinsan on 2010-01-02
> **wieman01 said:**
> If you are a day-to-day user, I would not recommend version 10.04 because it is still alpha. I would rather user 9.10 which will save you a lot of trouble.
+1 for it. Use 9.10 It's stable.. :)

---

### Post by ronacc on 2010-01-02
As others have stated lucid (10.04) is early alpha and all kinds of problems will arise. So if you are trying to do something productive use 9.10.  But I have another question , why not use OpenOffice instead of windows office + wine ?

---

### Post by VMC on 2010-01-02
> **ronacc said:**
> ...why not use OpenOffice instead of windows office + wine ?

I would agree, unless the OP has some bazaar formatting or some other Office product that OO can't handle.

---

### Post by ronacc on 2010-01-02
I'm sure that one of the reasons MS keeps monkeying with the formating in windows office (besides forcing you to buy$$$ the latest version) is just to screw with OO .

---

### Post by wieman01 on 2010-01-02
> **ronacc said:**
> I'm sure that one of the reasons MS keeps monkeying with the formating in windows office (besides forcing you to buy$$$ the latest version) is just to screw with OO .
Let's not go there, this is a genuine request for help, so let's try to stay on topic despite the fact that it's tempting to discuss the pros and cons of OO. :-)

---

### Post by ronacc on 2010-01-02
sorry , I'll try to resist taking cheap shots .

---

### Post by wieman01 on 2010-01-02
> **ronacc said:**
> sorry , I'll try to resist taking cheap shots .
:-) I had to bite my tongue as well.

---

### Post by VMC on 2010-01-02
> **aaydinalp said:**
> I have installed windows office 2007  successful when I try to run any office program like windows word or poweroffice wine says  it starting and then it gone

I don't know how to fix it
I am using ubuntu  10.04 alpha 1 and wine 1.2
please someone helps me

Another thing to try is using Wine through the terminal with Office and when it stops, see if anything left in the terminal that might help. I don't have Wine installed on this partition, but there may also be a log file that might be of help.

---

### Post by ronacc on 2010-01-02
I checked my wine install and didn't see any log files either in ~/.wine or /var/log . your suggestion of starting it from term might give him some clue , but looking at his join date and post count he is pretty new to be fighting with an alpha .

---

### Post by aaydinalp on 2010-01-03
I understand  all people  I actually d&#305;dn't want to  use microsoft  office but one of friend bring me pss file  and then  I couldn't open it because open  office says  I have to  move background picture or colour and  it is cryptic and then I have to install Microsoft  office 2007 
 Firstly I  got trouble with  Microsoft  office 2007 installation but I solved problem about installation problem  and then I tried to install Microsoft office 2007 again and then Microsoft office 2007 said  that I installed successful and then I go to my  wine  I try to open Microsoft office 2007  wiine says it is opening and then gone

If someone doesn't know how to solve problem and then  Tell me How can I install Microsoft Office 2007  with PlayOnLinux When I try t&#305;o use PlayOnLinux  It says can't find microsoft office 2007 cd

---

### Post by LKjell on 2010-01-03
> **aaydinalp said:**
> I understand  all people  I actually d&#305;dn't want to  use microsoft  office but one of friend bring me pss file  and then  I couldn't open it because open  office says  I have to  move background picture or colour and  it is cryptic and then I have to install Microsoft  office 2007 
 Firstly I  got trouble with  Microsoft  office 2007 installation but I solved problem about installation problem  and then I tried to install Microsoft office 2007 again and then Microsoft office 2007 said  that I installed successful and then I go to my  wine  I try to open Microsoft office 2007  wiine says it is opening and then gone

If someone doesn't know how to solve problem and then  Tell me How can I install Microsoft Office 2007  with PlayOnLinux When I try t&#305;o use PlayOnLinux  It says can't find microsoft office 2007 cd


For wine related issue Ubuntu forum would not be the best to look for solutions. Always try WineHQ first for their huge database. It is there for a reason. You just need to test different version of wine. If it does not work then it just does not work. 

Microsoft is happy when it does not work so they will not fix it. Then we find other way to fix. Like installing Windows on virtual box and install Office there. Or learn to use and promote other tools.

reference:
[http://appdb.winehq.org/appview.php?iVersionId=4992](http://appdb.winehq.org/appview.php?iVersionId=4992)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12811)

PS - If you have the chance try out LaTeX.

---

### Post by ronacc on 2010-01-03
did you install microsoft office from wine , or did you install it then try to oen it with wine ? I believe you need to install it from wine .

---

### Post by aaydinalp on 2010-01-04
how can I install wine like complate version again I deleted all c: folder from  wine and then I can't use browse C:\ driver what can &#305; do I want to fix my wine and upgrade too
I also upgrade  from ubuntu 9.10  from ubuntu 10.04 alpha but my computer says it is still 9.10 ubuntu why?

---

### Post by LKjell on 2010-01-04
> **aaydinalp said:**
> how can I install wine like complate version again I deleted all c: folder from  wine and then I can't use browse C:\ driver what can &#305; do I want to fix my wine and upgrade too
I also upgrade  from ubuntu 9.10  from ubuntu 10.04 alpha but my computer says it is still 9.10 ubuntu why?

Wine use env WINEPREFIX to set the system folder. The default is $HOME/.wine
So if you want to clean and reset wine you can either delete the folder $HOME/.wine and run "winecfg" in a terminal to create the it again. Or you can set WINEPREFIX to another folder and run winecfg. Though this is a bit complicated since you can only use a terminal with that WINEPREFIX to install stuff on.
```
export WINEPREFIX="/home/YOUR_USERNAME/LOCATION"
winecfg &
wine "PATH TO INSTALL"
```

****************'

To check what Ubuntu release you are using use ```
lsb_release -a

``` in a terminal and not the System > About Ubuntu ; since the documentation is not yet finish.

---


---
title: "Matlab R2010b is not working!!!!!!!!"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by sherbieny on 2010-11-11
Hello everyone,

This is my first post and my first issue with ubuntu 10.10

I installed matlab Unix R2010b which was on an image file and the installation went smoothly 
except that I chose the custom installation and during the installation steps it didn't ask me "Create symbolick links to MATLAB scripts" it just went from the installation directory to INSTALL

so after so many trials I managed to create a desktop Icon using 
[sudo wget [http://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png](http://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png) -O /usr/share/icons/matlab.png]

and 
[sudo wget 'https://help.ubuntu.com/community/MATLAB?action=AttachFile&do=get&target=matlab-r2010b.desktop' -O /usr/share/applications/matlab.desktop]

anyway I tried many command lines in the terminal and all failed telling me (bash: ..... Permission denied)

and when I used the desktop icon that I downloaded and properly linked to the matlab file inside the /bin directory it gave me this: (Details: Failed to execute child process "/media/86D061A9D061A063/Matlab/R2010b/bin/matlab" (Permission denied))

also I changed my account to administrator so that I would have the permission but it didn't change a thing

so Please help me with this because I need to work on matlab for my graduation project and I'm new to ubuntu so please try to be clear

thanks :D

---

### Post by sherbieny on 2010-11-13
People!!!

is there no one here had this problem or does know the solution

please guys help me out

---

### Post by marin123 on 2010-11-13
try installing octave and qt-octave.. its almost the same thing...

---

### Post by sherbieny on 2010-11-14
Does Octave do the same functions of Matlab?

and whats qt -octave?

anyone who knows the issue with matlab ?

---

### Post by marin123 on 2010-11-14
qt-octave is a graphical frontend for octave (it looks exactly like matlab). as far as i have used it, octave has the same syntax like matlab and can even run m-files.

---

### Post by a36233 on 2010-12-06
Octave doesn't have high-end tools like matlab (eg. sisotool, simulink, and so on...) for basic purposes it does the same things and it's free ;)

I have matlab r2010b instaled and I can start it normally with no problem, if you start it outside of terminal you need to add -desktop flag (eg shortcuts)

Try to reinstall it follow the install manuals.

---

### Post by jakkamgirish on 2010-12-24
if i used wine its not working ... how can i use malab i hav many projects to work on !

---


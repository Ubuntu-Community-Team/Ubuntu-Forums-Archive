---
title: "Matlab 2020b doesn0t run after installing on Ubuntu 20.14 LTS"
date: 2021-02-23
forum: Installation &amp; Upgrades
---

### Post by jair0799 on 2021-02-23
Hi there, I'm a nwe Ubuntu user. I installed Matlab 2020b by downloading the .zip in the oficial website, after installing I added the Matlab Scientific Computing enviroment from the Ubuntu store, but after all the Matlab doesn't run. What could I do? 
Only to clarify, I already have GNU Octave installed in my computer. It's almost the same, but I really wante to run Matlab in Ubuntu. I hope you can help me.

---

### Post by CelticWarrior on 2021-02-24
[https://www.mathworks.com/matlabcentral/answers/518584-how-do-i-install-on-ubuntu](https://www.mathworks.com/matlabcentral/answers/518584-how-do-i-install-on-ubuntu)

---

### Post by jair0799 on 2021-02-24
I checked that guide, Mathlab is already installed but it doesn't run. I've tried installig Matlab three times with different versions (2020a,2020b,2019b), but I still having the same problem.

When I try to open Matlab, It seems to be charging but after that nothing happens.

---

### Post by #&amp;thj^% on 2021-02-24
Sometimes it's as easy as:
```
sudo chown YourUsername -R ~/.matlab
```
Of course change "YourUsername" to your real user name.
Or a good place to start trouble-shooting: [https://matlab.fandom.com/wiki/FAQ#After_installation.2C_MATLAB_crashes_or_gives_an_error_message_when_I_try_to_run_MATLAB](https://matlab.fandom.com/wiki/FAQ#After_installation.2C_MATLAB_crashes_or_gives_an_error_message_when_I_try_to_run_MATLAB)

A compiled matlab executable normally comes with a "run_XXX.sh", which sets the LD_LIBRARY_PATH. 
If that still gives no joy run "matlab" in a terminal and copy any output generated paste back here, might shed some light.

---

### Post by jair0799 on 2021-02-24
I run te Code with out problem, but the app doesn't run.

I tried to run the program with the terminal and dropped me this error.

```
/usr/local/MATLAB/R2020b/bin/glnxa64$ sudo ./MATLAB[sudo] contraseña para jair: 
License checkout failed.
License Manager Error -9
Your username does not match the username in the license file. 
To run on this computer, you must run the Activation client to reactivate your license.


Troubleshoot this issue by visiting: 
https://www.mathworks.com/support/lme/R2020b/9


Diagnostic Information:
Feature: MATLAB 
License path: /root/.matlab/R2020b_licenses:/usr/local/MATLAB/R2020b/licenses/license.dat:/usr/local/MATLAB/R2020b
/licenses/license_jair-desktop_40513311_R2020b.lic 
Licensing error: -9,57.

 
```

The messages in the oficial website suggest that the best way to correct the -9 Error is by reactivating Matlab. So I run this Code in the /bin folder and I reactivate Matlab.
 ```

/usr/local/MATLAB/R2020b/bin$ sudo ./activate_matlab.sh

```
 After all, when I try to run Matlab by the Terminal, it returns my the same error.

---

### Post by #&amp;thj^% on 2021-02-24
here: [https://www.mathworks.com/matlabcentral/answers/93703-why-do-i-receive-host-id-error-after-selecting-a-license-file-during-installation](https://www.mathworks.com/matlabcentral/answers/93703-why-do-i-receive-host-id-error-after-selecting-a-license-file-during-installation)

---

### Post by ActionParsnip on 2021-02-24
> **1fallen said:**
> Sometimes it's as easy as:
```
sudo chown YourUsername -R ~/.matlab
```


If you use:

```

sudo chown $USER -R ~/.matlab

```

It will save the user confusion. BASH variables are your friends

---

### Post by #&amp;thj^% on 2021-02-24
> **ActionParsnip said:**
>  BASH variables are your friends

I'm aware of that ;), Staff at metlab recommends real names, due to the various installs.

---


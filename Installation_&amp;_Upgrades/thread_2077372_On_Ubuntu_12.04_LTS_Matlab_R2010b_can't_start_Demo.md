---
title: "On Ubuntu 12.04 LTS Matlab R2010b can't start Demos through firefox or google-chrome"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by RLDr on 2012-10-28
I have installed Matlab 7.11 (R2010b) on Ubuntu 12.04 LTS successfully.
I can run installed matlab from command line or from created desktop link.
But I can't run matlab demo video files through firefox or google-chrome or chromium-browser. Actually I can't start any browser (system default) to view a webpage from matlab (and also from matlab command prompt).

Please tell me your solution method if you had faced similar problem earlier.

Thanks in advance.

---

### Post by RLDr on 2012-11-09
I solved my above problem after extensive searching through the web and tired-less experimenting with the matlab installation. :D Below is the most easy method to solve. It will be helpful to you if you face the same problem in the future.

Start matlab using sudo, plus giving full path to the matlab executable, e.g. give the following command in terminal according to path (change if your path to matlab executable is different)
sudo /usr/local/MATLAB/R2010b/bin/matlab

After starting matlab goto File > Preferences and under the "System Web browser" section, change the command firefox to sudo firefox
Click on Apply, then OK.
Exit matlab.

From now, everytime start matlab using
sudo /usr/local/MATLAB/R2010b/bin/matlab

Now click on demo or any other outward links from within matlab. Firefox will open your matlab links successfully.

Note: Your MATLAB Preferences are saved in the file 'matlab.prf' located in /home/user-name/.matlab/R2010b folder. You can change the default settings for matlab by editing (using sudo gedit) this file also.
Search for HTMLSystemBrowser=Ssudo firefox

---

### Post by northcamel on 2013-01-18
> **RisingMan said:**
> I solved my above problem after extensive searching through the web and tired-less experimenting with the matlab installation. :D Below is the most easy method to solve. It will be helpful to you if you face the same problem in the future.

Start matlab using sudo, plus giving full path to the matlab executable, e.g. give the following command in terminal according to path (change if your path to matlab executable is different)
sudo /usr/local/MATLAB/R2010b/bin/matlab

After starting matlab goto File > Preferences and under the "System Web browser" section, change the command firefox to sudo firefox
Click on Apply, then OK.
Exit matlab.

From now, everytime start matlab using
sudo /usr/local/MATLAB/R2010b/bin/matlab

Now click on demo or any other outward links from within matlab. Firefox will open your matlab links successfully.

Note: Your MATLAB Preferences are saved in the file 'matlab.prf' located in /home/user-name/.matlab/R2010b folder. You can change the default settings for matlab by editing (using sudo gedit) this file also.
Search for HTMLSystemBrowser=Ssudo firefox

Thanks, Solve my problem!

---


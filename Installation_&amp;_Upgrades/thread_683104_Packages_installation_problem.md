---
title: "Packages installation problem"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by jsentianus on 2008-01-30
I have marked some packages in synaptic package Manager that I need to installed. After that clicked the "apply" button. At the bottom of the synaptic package manager panel, there are list of packages that ..eg..installed, broken, to install/upgrade, to remove. My problem is all the packages that I would like to install are still not installed (I presumed) as all of them are still with status "to install". Normally the installed package will be indicated with "blue" box on the "S" column and also would list out the installed version. In my case this was not happen.

For example I would like to install g++, And when I checked at the terminal by just typing "whereis g++" , I couldn't find the g++. 

Can anyone have an idea, how to install the packages? (I thought i have done the right way)

---

### Post by taurus on 2008-01-30
Close synaptic or Add/Remove if you have it open.  Then, run

```
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```
You need the build-essential package if you need gcc/g++ compiler.

---


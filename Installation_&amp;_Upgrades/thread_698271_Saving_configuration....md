---
title: "Saving configuration..."
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by sorfrena on 2008-02-16
Hi,

I am going to format my hd and I wanted to know if there's any way for saving my pc configuration. I don't want to save everything...I just would like something to keep memory of all the things I installed, in order not to repeat the same steps once formatted.
One example for all...I installed amsn and I wonder if there is any method to install it in an automatic manner...without going in add/remove packages and adding it manually. I know it's simple, but when you have 10s or maybe 100s packages installed it can be frustrating. Moreover I installed some packages manually...and that costs more time. 
I tried a utility called APTonCD, but it seems that it just saves all the packages installed...I don't know how to use it to even install all the saved packages. Moreover I am not going to change my pc...I am just going to format, so that my pc configuration is not going to change.

Thanks for your help,
Freddy

---

### Post by TheWizzard on 2008-02-16
Make a list of instaaled software: 
$ dpkg --get-selections | grep -v deinstall > installed-software.log

restore system:
# dpkg --set-selections < installed-software.log


[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

### Post by TheWizzard on 2008-02-16
it also helps to backup /etc

---

### Post by sorfrena on 2008-02-16
Well...I myself am trying to answer the question.
I realized that APTonCD ''when trying to restore'' copies by default all the deb files to the /var/cache/apt/archives dir. So now I have this beautiful big dir with all the packages I need. 
I saw that the command sudo dpkg -i filename.deb installs the package .deb...so I realize that what I need now is a script to install all the .deb files...but it seems to be less easy cause of dependencies...right?
I have seen that sometimes the installation completes successful, others not...saying for example (zattoo depends on libgtkglext1; however:
  Package libgtkglext1 is not installed.)

So I was thinking of a for loop that visits all the .deb files of the dir, and tries to execute the instruction sudo dpkg -i filename.deb. I think that I need even any method to see if the installation was successful...(how?)...so that I can come back later on that package
I'll try to express me better with a pseudocode

int number_of_packages=number of .deb files
int number_of_packages_installed =0;//number of installed packages...0 at the beginning
while (number_of_packages_installed < number_of_packages){
   for (visit all .deb files){
      sudo dpkg -i filename.deb
      if (installation_successful)
         number_of_packages_installed++;
      }
   }

this way should allow to visit the same packages more times till all the dependencies are resolved...so it can be installed...i suppose
any idea on how to implement this? can it work?
really thanks

---

### Post by TheWizzard on 2008-02-16
th solution above should do the trick. 
put your .deb files in a local repository. then you won't have to download everything. 

but you can also give your pseudocode a try. looks interesting. please post the results!

---

### Post by sorfrena on 2008-02-16
Yeah...the problem is that I have never programmed in linux...I needed a help
I think I am going to try the solution you told me...if I put all .deb files in the same dir how can I tell him not to download them all again?
thank you

P.S.: if anyone that knows a bit about linux programming can help me to implement my pseudocode...he's wellcome, thanks

---

### Post by TheWizzard on 2008-02-16
> **sorfrena said:**
> Yeah...the problem is that I have never programmed in linux...I needed a help
I think I am going to try the solution you told me...if I put all .deb files in the same dir how can I tell him not to download them all again?
thank you


search for local repository. i never used this, so i can't help you here.

---


---
title: "building ubuntu kernel"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by eldragon on 2008-09-11
ive been building my own kernel with the following guide:[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

but instead of using kernel.org's kernel, ive used the kernel downloaded with apt-get install linux-source-2.6.24 since im trying to get the exact ubuntu kernel, with some extra patches applied.

if i understand correctly, copying the config file from my current kernel /boot/config-`uname -r` /usr/src/linux/.config will pick all options used for the current kernel..am i correct?

the thing is the end result is way different. for example, i have to enable alsa sound support with make menuconfig, in the sound section in order to get sound to work. this is ONE example.

another example, is my webcame drivers arent being included in the new kernel. 

so. are there any extra steps im missing in order to get the exact kernel features in the ubuntu kernel, but with some minor customizations? 

im not that keen on kernel compiling, so bare with me if im being quite noobish.

PS. if you are wondering why i need to build the kernel, read: [http://bugzilla.kernel.org/show_bug.cgi?id=9905](http://bugzilla.kernel.org/show_bug.cgi?id=9905)

---

### Post by eldragon on 2008-09-11
bumping + extra info

ive managed to find out which is the module required to get the webcam running and downloaded and built its source. so all is well. im still wondering why i needed to do all this though.

same thing happened with alsa, had to compile my own modules, since the ones included with the source didnt work as expected.

---

### Post by the_burk on 2008-09-12
if you do know what module you need for the webcam .. in menuconfig xconfig or whichever config you use .. you can choose to make that module when you compile the kernel ... and then make a make modules-install and it will do it for you ...

 thats what the config tool is about... find out witch modules you need and compile them.. not any extras that you dont use .. eg no scsi drivers if you dont use scsi ... no modules for every single set of network cards and so on ... witch the kernel guys do when they are trying to get as many ppl as possible on the same kernel ... 

and the less stuff you compiled the computer got more memory to play with .. less kernel code to have in the memory.. therefore a faster computer.. (with more hd space.. )

before you remove anything .. make sure your not using it .. otherwise you might end up with a computer that does nothing.. '


so ALWAYS keep a backup of your old kernel if something ***** up ... 

good luck with the kernel hacking.. :)

btw .. when compiling bring a good tv set a couple of your favorite movies and some beers... you are going to wait for a while.. ;)

---

### Post by eldragon on 2008-09-12
> **the_burk said:**
> if you do know what module you need for the webcam .. in menuconfig xconfig or whichever config you use .. you can choose to make that module when you compile the kernel ... and then make a make modules-install and it will do it for you ...

 thats what the config tool is about... find out witch modules you need and compile them.. not any extras that you dont use .. eg no scsi drivers if you dont use scsi ... no modules for every single set of network cards and so on ... witch the kernel guys do when they are trying to get as many ppl as possible on the same kernel ... 

and the less stuff you compiled the computer got more memory to play with .. less kernel code to have in the memory.. therefore a faster computer.. (with more hd space.. )

before you remove anything .. make sure your not using it .. otherwise you might end up with a computer that does nothing.. '


so ALWAYS keep a backup of your old kernel if something ***** up ... 

good luck with the kernel hacking.. :)

btw .. when compiling bring a good tv set a couple of your favorite movies and some beers... you are going to wait for a while.. ;)

thanks, yes, i know about this, in fact, i didnt plan to remove anything just to be on the safe side, especially since most stuff is being built as a module, i thought i could live with some mbytes lost.

first thing, the source for that particular module (gspca) was not available with the kernel source. i thought it would since its being shipped with the ubuntu binary kernel. (aka. with stock kernel, camera loads fine, with built kernel, had to download the debian source code and build that).

i thought the whole point of downloading ubuntu's source was to get the extact source base they used to build the stock kernel.

so question now is: how do i get that source?

PS. i do build overnight on a spare computer outside my room :D

---


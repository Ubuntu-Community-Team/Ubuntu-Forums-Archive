---
title: "Installation Pain"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by mingyeow on 2006-02-20
Hi folks,

sorry, but i am getting pretty frustrated with Linux here, hoping you guys can help me out….

mingyeow@u0201218:~/Desktop$ sudo dpkg -i install adobereader-enu_7.0.5-1_i386.deb
dpkg: error processing install (–install):
cannot access archive: No such file or directory
(Reading database … 60679 files and directories currently installed.)
Preparing to replace adobereader-enu 7.0.5-1 (using adobereader-enu_7.0.5-1_i386.deb) …
Unpacking replacement adobereader-enu …
Setting up adobereader-enu (7.0.5-1) …

Errors were encountered while processing:
install
mingyeow@u0201218:~/Desktop$

I have generated a deb file already, but what is wrong such that i cannot install? Afterwards, the app shows up in my app list but it cannot run propertly. 

Can I also ask -- how do i add an application via synpatic? Do i keep it in the repository? If so, where is it?

Lastly, how do i install from a JAR file? I tried running stuff like java -jar but i always get weird errors

---

### Post by el3ktro on 2006-02-20
dpkg -i install won't work, the syntax is simply dpkg -i <package>. But why do you want to install this package manually, you can use Synaptic to automatically install this for you - thats so much easier. You just need the right repositories.

Tom

---

### Post by jsestri2 on 2006-02-20
I've never heard of installing from a JAR file...

There are two options as to what i guess it could mean though.

A) The jar is excuteable, and you need to pass something like:
java whatever.jar
or
java -classpath whatever.jar CLASSNAME

to figure out what class name you'd have to know the contents of the jar file. (see idea B)

B) More likely, this is just a bunch of files compressed with the jar format essentially ZIP with some other stuff. To open those, you need the Java SDK, (available at the SUN website.) You use the tool "jar" something like this to extract files similar to gunzip or tar:

jar -xnf whatever.jar

---

### Post by mingyeow on 2006-02-20
hi, thanks 4 e reply! I guess that is what i do not understand -- how to I do add to the synaptic repository? Also, i get an error when trying to run program. it takes only about 2 seconds to install, which is impossible. How do i uninstall?

M

---


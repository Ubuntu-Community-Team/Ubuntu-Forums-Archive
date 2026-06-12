---
title: "Adept and synaptic"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by sanchan89 on 2008-11-10
Hey,
I have been using Ubuntu 8.04 for the past few months, and I had installed a neat collection of packages. I do not have an internet connection and all this time I have been installing stuff offline by pasting the required debians in the /var/cache/apt/archives folder.

I thought sudo apt-get can still install the packages offline if I pasted the debs in the same folder in Kubuntu 8.10. But thats not working. For eg., sudo apt-get install sun-java6-jdk wouldn't install though it had done so perfectly in Ubuntu, when I had put the same set of files in the folder.

Can't I re use the downloaded debs now? Leave the gtk based softwares, at least the development libraries?

---

### Post by Partyboi2 on 2008-11-11
To install debs that you have downloaded from the net, you can either double click on the deb package or open a terminal and cd to where the debs are and install them with
```
sudo dpkg -i package
``` change package to actual name of deb. Another option you can try is to use a program called [[COLOR=Blue]keryx[/COLOR]]("http://keryx.betaserver.org/") to download packages you want.

---

### Post by sanchan89 on 2008-11-11
Thanks for the info,

I have a lot of packages and each of them has a lot of dependencies. Back in Ubuntu, all I needed to do was to put them in the /var/cache/apt/archives ( I guess that's where Synaptic stores the packages it downloaded ) and type ```
sudo apt-get install <package with multiple dependecies>
```, and the software and all its dependencies would be installed from the local repository.

Is there no equivalent way of doing it in Kubuntu?
Alternately, does Adept save the downloaded packages in the FileSystem? If so where?

---

### Post by DarkDemonNT on 2008-11-11
> Sometimes you have lots of packages .deb that you would like to use APT to install so that the dependencies would be automatically solved.

To do that create a directory and put the .debs you want to index in it . For example:

     # mkdir /root/debs

You may modify the definitions set on the package's control file directly for your repository using an override file. Inside this file you may want to define some options to override the ones that come with the package. It looks like follows:

     package priority section

package is the name of the package, priority is low, medium or high and section is the section to which it belongs. The file name does not matter, you'll have to pass it as an argument for dpkg-scanpackages later. If you do not want to write an override file, just use /dev/null. when calling dpkg-scanpackages.

Still in the /root directory do:

     # dpkg-scanpackages debs file | gzip > debs/Packages.gz

In the above line, file is the override file, the command generates a file Packages.gz that contains various information about the packages, which are used by APT. To use the packages, finally, add:

     deb file:/root debs/

After that just use the APT commands as usual. You may also generate a sources repository. To do that use the same procedure, but remember that you need to have the files .orig.tar.gz, .dsc and .diff.gz in the directory and you have to use Sources.gz instead of Packages.gz. The program used is also different. It is dpkg-scansources. The command line will look like this:

     # dpkg-scansources debs | gzip > debs/Sources.gz

Notice that dpkg-scansources doesn't need an override file. The sources.list's line is:

     deb-src file:/root debs/
Hope this help.

[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html)

---


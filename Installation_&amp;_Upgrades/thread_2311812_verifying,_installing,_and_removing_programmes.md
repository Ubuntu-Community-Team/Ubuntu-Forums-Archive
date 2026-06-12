---
title: "verifying, installing, and removing programmes"
date: 2016-01-30
forum: Installation &amp; Upgrades
---

### Post by anon_private on 2016-01-30
How can I check the integrity of a package using its HSA1 signature?

If I have programme on my hard drive will sudo install pacckage name install the programme?

If I decide to remove the programme will sudo remove programme be sufficient - will it remove all the associated files?

Thanks

Ps kubuntu

---

### Post by matt_symes on 2016-01-30
Hi

> **anon_private said:**
> How can I check the integrity of a package using its HSA1 signature?


Do you mean the SHA1 signature  ?

If so then you can use the binary sha1sum.

Here's an example
```

matthew-xu-16-04:/home/matthew:0 % sha1sum tmp.txt
9cb0f11421704bf2b20ffc6b4facf1d2116ca209  tmp.txt
matthew-xu-16-04:/home/matthew:0 %
```

You can compare the SHA1 signature generated to whichever SHA1 reference  signature you are using for that package or file.

Be aware that there are other hashing algorithms though, such as the SHA2 suite and MD5.

```
matthew-xu-16-04:/home/matthew:0 % sha256sum tmp.txt 
6cd7b10f22f400b314e9f505b3aed64b09915d1e1dbc663e9ead94bc3c3920a0  tmp.txt
matthew-xu-16-04:/home/matthew:0 % sha512sum tmp.txt 
dd5dc40d947522fe2a595fd3581a64446e4aed00aa4dcff6b25df5bfacc2c2f68096281fb23d803057ca38c5d4261b2b6a10a5f7d11a2f639a861ddbef4205a5  tmp.txt
matthew-xu-16-04:/home/matthew:0 % md5sum tmp.txt 
b57d82cda6c630bdfcb28843ad7e52fe  tmp.txt
matthew-xu-16-04:/home/matthew:0 %
```

Make sure you are generating and comparing the correct hash type.

> If I have programme on my hard drive will sudo install pacckage name install the programme?

No. *apt-get install* will only install packages from repositories.

You need to use...

```
sudo dpkg -i <package_name>.deb
```

...,when in the same directory, to install the package on your hard drive.

> If I decide to remove the programme will sudo remove programme be sufficient - will it remove all the associated files?

```
sudo apt-get remove <package_name>
```

will remove most files but it will (usually) leave the packages configuration files on the installation.

To attempt to completely remove a package, you need to use the purge option.

```
sudo apt-get purge <package_name>
```

Kind regards

---

### Post by Dennis N on 2016-01-30
> If I have programme on my hard drive will sudo install pacckage name install the programme?

No, currently, Ubuntu uses the Debian package management system (which requires .deb packages for applications). In that, dpkg is at the base level to install, remove, and provide information about .deb packages. Higher level programs apt and Synaptic Package Manager (which directly or indirectly invoke dpkg for installing) are also able to fetch and manage packages and dependencies.

Small guide to using apt here:
[https://www.digitalocean.com/community/tutorials/how-to-manage-packages-in-ubuntu-and-debian-with-apt-get-apt-cache](https://www.digitalocean.com/community/tutorials/how-to-manage-packages-in-ubuntu-and-debian-with-apt-get-apt-cache)

Google for other guides, or "how to use Synaptic Package Manager". Many guides are available.

---

### Post by anon_private on 2016-01-31
Thank you for replying.

Firstly, I am trying to verify a package using its signature file.

I am making an error in the command line:

andrew@andrew-Dell-DM061:~/Downloads$ gpg --verify master-pdf-editor-hash-SHA1.sig master-pdf-editor-3.5.81_i386.deb
gpg: can't open `master-pdf-editor-hash-SHA1.sig'
gpg: verify signatures failed: file open error
andrew@andrew-Dell-DM061:~/Downloads$ 

Secondly:

Am I correct that under kubuntu I can only install Debian files? I expect the answer is no.

If I have a file on my system that I wish to install I must use:

sudo dpkg -i package.deb.

If I want to remove this package, I must use:

sudo apt-get remove package.deb

I am a little confused by the latter command. The package is on my systems, I am not attempting to use the repository. I would of thought that apt-get means downloading from the repository!.

Finally.

Is Debian just a file system architecture. I often see people talking of Debain files. I am using kubuntu, part of the Linux family, i would have through that I could install any Linux application, Debain or not?

Best wishes

---

### Post by Dennis N on 2016-01-31
> If I have a file on my system that I wish to install I must use sudo dpkg -i package.deb

We end users doesn't commonly invoke dpkg directly to install/remove software. We use apt-get, the Ubuntu Software Center, or Synaptic Package Manager. Another good tool to install downloaded .deb files is the gdebi package installer. All these utilize dpkg (and apt-get) in the background.

Read more here:

[http://unix.stackexchange.com/questions/159094/install-from-a-deb-file-by-dpkg-i-or-by-apt](http://unix.stackexchange.com/questions/159094/install-from-a-deb-file-by-dpkg-i-or-by-apt)

As this article says, dpkg doesn't resolve the dependencies needed for your program to work - apt-get does.

**gdebi** package installer is in the Ubuntu repositories (as gdebi). It also resolves dependencies.

note that **apt** is a package manager, **apt-get** is a command-line tool used with it; there are other related commands, like **apt-cache**. the apt-get command is not just for downloading - it depends on the option following the command.

More about APT:

[https://en.wikipedia.org/wiki/Advanced_Packaging_Tool](https://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

---

### Post by oldos2er on 2016-01-31
> **anon_private said:**
> I am making an error in the command line:

andrew@andrew-Dell-DM061:~/Downloads$ gpg --verify master-pdf-editor-hash-SHA1.sig master-pdf-editor-3.5.81_i386.deb
gpg: can't open `master-pdf-editor-hash-SHA1.sig'
gpg: verify signatures failed: file open error
andrew@andrew-Dell-DM061:~/Downloads$ 


I think you'd run ```
sha1sum master-pdf-editor-3.5.81_i386.deb
``` and check the result against the SHA1 hash on their website.

> **anon_private said:**
> Am I correct that under kubuntu I can only install Debian files? I expect the answer is no. The package manager (APT) only understands *deb files, but you can install from source code, or download and install already compiled programs from the internet, if you trust their source.

> **anon_private said:**
> If I have a file on my system that I wish to install I must use:

sudo dpkg -i package.deb.

If I want to remove this package, I must use:

sudo apt-get remove package.deb You can use *sudo dpkg -r <program>*. 

> **anon_private said:**
> Is Debian just a file system architecture. I often see people talking of Debain files. I am using kubuntu, part of the Linux family, i would have through that I could install any Linux application, Debain or not? Debian is an old and well-established Linux distro ([file system architecture]("http://tldp.org/LDP/intro-linux/html/sect_03_01.html") is something completely different) with large repositories. If you have a question about installing a particular application (not in the repositories?) it would be best to start a new thread.

---

### Post by matt_symes on 2016-01-31
Hi

You're mixing up a couple of concepts and Dennis N's and oldos2ers' post are good posts to help clarify these concepts. I just though i would add some points to help as well.

Most packages installed on Ubuntu are debian packages. These packages are .deb files like the one you mentioned in your first post.

These debian packages are compressed archives, similar but not identical to zip files, that contain the not only files (binaries, scripts, configuration and other files such as man pages) the program needs to run but also metadata files that specifies where on the system to put the files. 

As an example, these metadata files may specify that the packages binaries may be stored in /usr/bin and configuration files may be stored in /etc.

These debian files are manipulated using the *dpkg* command.

To install a debian package you would use

```
sudo dpkg - i <package_name>.deb
```

and to remove a package to would use

```
sudo dpkg -r <package_name>.deb
```

To purge a debian package you would use

```
sudo dpkg -P <package_name>.deb
```
 
Most debian packages also need other debian packages to run. These extra debian packages are called dependencies.

This is, in part, where *apt* comes into play. When you install a package using *apt-get install*, apt will work out what package you are trying to install and download it from the Internet (from a repository or a PPA).

But more than that, apt will also work out what dependencies (other debian packages) the package you are trying to install needs. Any dependencies that the packages needs that are not already installed on you system, apt will download them for you.

*apt* then call dpkg (along with a number other commands) to install the actual package and its dependencies for you.

Before the days of apt, you had to download each debian package you wanted to install and any dependencies that packages may have had manually, and then install them yourself in the correct order.

apt automates this task. As apt sits on top of dpkg, removing packages using *apt-get remove* or *apt-get purge* will remove or purge those packages by calling into dpkg's remove or purge command. It'll also attempt to remove any other packages that it thinks it can safely remove that may have been dependencies of that package.

Because apt is not perfect at removing dependencies when uninstalling packages, there is the command *apt-get autoremove* to help with that task.

The dpkg suite of commands and the apt suite of commands can do far more than i outlined above, however it gives you a general idea.

*apt* itself handles the downloading of packages. It verifies those packages using public key cryptography and hashes. It generates hashes for downloaded packages and compares them against known good hashes that it also downloads. 

What you are doing when you are manually checking hashes is a function that apt performs automatically for you.

Hashing to used to verify that the package was not corrupted while it was being downloaded and also to verify that the package has not been tampered with by any, potentially malevolent, third party.

This whole process is validated at the top level using public key cryptography, similar but not identical to, the public key cryptography used in https.

The above is a pretty high level explanation of dpkg and apt. A lot more actually goes on under the hood but in broad brush stokes, that's what happens.

If you have any more questions then feel free to ask.

Kind regards

---

### Post by matt_symes on 2016-01-31
Hi

I thought i would expand on your other questions but i didn't want to muddy the waters of my previous post, hence two consecutive posts.

> Am I correct that under kubuntu I can only install Debian files? I expect the answer is no.

Yep. The answer is no :)

The main package manager in debian is apt/dpkg. Debian derivatives such as Ubuntu, Xubuntu, Kubuntu and Lubuntu have inherited debian's package manager.

Other different distributions, such as Fedora and Red Hat, use a different package manager called yum (now being superseded in Fedora by DNF). yum uses .rpm packages in the same way that apt uses .deb packages.

It's possible to convert and install a .rpm package to a .deb package using the command *alien*. This is not alway successful though. A description of alien is given below. 

```
matthew-xu-16-04:/home/matthew:2 % acse ^alien$
alien - Convert and install rpm and other packages
matthew-xu-16-04:/home/matthew:2 %
```

Other distributions have other package managers and it may *sometimes* be possible to install packages from these distributions.

Generally you want to stick to the native packages your package manager uses.

Another way to install software, is to built and install them yourself from the source code. Instructions on how to build a particular software package are usually included with the source code. This entails setting up a build environment for the software package.

Installing software this way usually bypasses apt and dpkg and uses typically, *./configure*, *make* and *sudo make install*, although there is a way to build a .deb file from the source code that you can install using dpkg.

So, there are other methods to install software on Ubuntu and the above list is not exhaustive.

Usually though, you'll want to use .deb files obtained via apt and sourced from a repository or a PPA.

> 
Is Debian just a file system architecture. I often see people talking of Debain files. I am using kubuntu, part of the Linux family, i would have through that I could install any Linux application, Debain or not?

The term may be more enlightening if called 'debian package files'; package files containing files (binaries and the like) that are to be installed on the filesystem.

Kind regards

---

### Post by matt_symes on 2016-01-31
Hi

One final post :)
> 
I am making an error in the command line:

andrew@andrew-Dell-DM061:~/Downloads$ gpg --verify master-pdf-editor-hash-SHA1.sig master-pdf-editor-3.5.81_i386.deb
gpg: can't open `master-pdf-editor-hash-SHA1.sig'
gpg: verify signatures failed: file open error
andrew@andrew-Dell-DM061:~/Downloads$ 

Did you download the signature file and did you download it to your ~/Downloads directory ? 

That error message usually means that gpg cannot find the signature file.

Kind regards

---

### Post by anon_private on 2016-02-01
Thanks to all for the detailed responses.

Just to check my understanding from the discussions.

There are two scenarios. Programmes that are in the kubuntu repository, and others that are not.

If I choose the install, remove, or purge a programme that is available from the repository, then the commands would be, for example, sudo apt-get remove package.

If I installed the package from my hard drive, I would use, for example, sudo dpkg - r package.

Am I correct?

---

### Post by matt_symes on 2016-02-01
Hi

> **anon_private said:**
> There are two scenarios. Programmes that are in the kubuntu repository, and others that are not.

Yes. ((1) Those programs in a repository or PPA and (2) those programs that are not). 

Kubuntu shares the same repositories as Ubuntu, Xubuntu and Lubuntu and of some the Ubuntu derivatives.

> If I choose the install, remove, or purge a programme that is available from the repository, then the commands would be, for example, sudo apt-get remove package.

Yes.

> If I installed the package from my hard drive, I would use, for example, sudo dpkg - r package.

This is also the case, yes.

If the package was not it the repositories and you downloaded a deb from the web and installed it using dpkg, you would need to remove it using dpkg.

One of the benefits of using apt over manually installing packages using dpkg is that you will get updates to the packages installed automatically when you run *sudo apt-get update* and *sudo apt-get upgrade* or when update-manager runs as the packages in the repositories are updated regularly.

This is, in part, the reason why using apt is by far the preferred method of installing packages on your system and is what you'll want to be doing for almost every package you install. 

BTW: The difference between remove and purge is that remove will usually keep the packages configuration files installed whereas purge will usually remove everything.

Also, as Dennis N pointed out, there are graphical programs that can be used to manage packages such as gdebi and software-center. The reason i tend to post terminal commands is because i may not be familar with the desktop environment that someone else is using. 

If you feel this has answered your questions then please mark this thread as SOLVED using the thread tools menu above post #1.

It'll help other looking for similar information and is a simple way you can give back to the community.

Kind regards

---

### Post by anon_private on 2016-02-03
Thank you for responding.

In the main, I download software from the repository. Using kubuntu, I access the repository via muon. I don't have access to the ubuntu repository, or any of the other flavours of ubuntu - as far as I know..

If I notice a programme that is not in the repo, then I will download and install it - no other choice.

I will mark the thread as SOLVED, and hope that others will gain information from all the detailed responses.

Best wishes.

---


---
title: "xrt : Depends: dkms (&gt;= 2.2.0) but it is not going to be installed broken packages"
date: 2021-03-09
forum: Installation &amp; Upgrades
---

### Post by goahead97 on 2021-03-09
Hello

I need to install a debian file in Ubuntu 18.04.4 by means of
 
```
sudo apt install ./xrt_202020.2.8.743_18.04-amd64-xrt.deb
```

but I get the following error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xrt' instead of './xrt_202020.2.8.743_18.04-amd64-xrt.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 xrt : Depends: dkms (>= 2.2.0) but it is not going to be installed
       Depends: uuid-dev (>= 2.27.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Then I tried to run this:
```
sudo apt install dkms

```

and I got the following error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 dkms : Depends: gcc but it is not going to be installed
        Depends: dpkg-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Then I tried to run this:
```
sudo apt install gcc

```

and I got this error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gcc : Depends: gcc-7 (>= 7.3.0-12~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I need to keep this Ubuntu release 18.04.4.

Does anyone have any idea or suggestion to be able to install the debian file in Ubuntu 18.04.4 without updating to a new release? 

Thanks

---

### Post by CelticWarrior on 2021-03-09
> [COLOR=#000000]I need to keep this Ubuntu release 18.04.4.[/COLOR]
No, you don't and it was [explained why]("https://ubuntuforums.org/showthread.php?t=2458698&page=2&p=14024091#post14024091") already.
And point releases are not meant to be "static", never were, never will.
There are a few valid reason for wanting to keep a certain kernel series - drivers or other software - but keeping a specific kernel series doesn't impact the subsequent update to newer release points because all a release point mean is [a more up-to-date ISO image]("https://ubuntuforums.org/showthread.php?t=2458809&p=14024231#post14024231") and that's why release points ONLY appear in LTS releases, releases that are supported for an extended period of time (3 to 5 years) therefore users benefit from not having to install tons of updates in one go. The newest release point includes all updates up to its release.

---

### Post by goahead97 on 2021-03-09
[COLOR=#222222][FONT=Verdana]Thanks for the information. [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Sorry, according to Xilinx website the only releases that are compatible with the 3 tools I need to use are Ubuntu 18.04.1, 18.04.2, 18.04.3 and 18.04.4[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]3 tools:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Alveo U50[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Alveo U280[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Vitis 2020.2[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Find as follows the links to the screenshots of the Xilinx website where the required operating systems for each tool get displayed:
[/FONT][/COLOR]**[COLOR=#000000][FONT=Arial][https://lh3.googleusercontent.com/lVzRkkuSeCDfLAliZyb_CoyjSXMN-zwd8cAoQJhPbf97fNzzQDo2vfR0xm8i07R4DcOc6H8sQtAV3Fk6XTpmMY6CYmXqjQCzOLWChpe_-fdzZIsndmB45Ef5hMDCmpss2gumkuVS](https://lh3.googleusercontent.com/lVzRkkuSeCDfLAliZyb_CoyjSXMN-zwd8cAoQJhPbf97fNzzQDo2vfR0xm8i07R4DcOc6H8sQtAV3Fk6XTpmMY6CYmXqjQCzOLWChpe_-fdzZIsndmB45Ef5hMDCmpss2gumkuVS)[/FONT][/COLOR]**

[B][COLOR=#000000][FONT=Arial][https://lh6.googleusercontent.com/yYwB8lPWhsVrQ3Aws-SXdGygKRoXHmjAjArlIvjlChR6RaqZdi8uqSaz64kUTmlQsD32O1V-VBNcejXbY5XC2PzSVzUt4SNNnHRwFbrEF3KNptnnXWbx9cDCYgfyDjyFenMRpUcJ](https://lh6.googleusercontent.com/yYwB8lPWhsVrQ3Aws-SXdGygKRoXHmjAjArlIvjlChR6RaqZdi8uqSaz64kUTmlQsD32O1V-VBNcejXbY5XC2PzSVzUt4SNNnHRwFbrEF3KNptnnXWbx9cDCYgfyDjyFenMRpUcJ)
[/FONT][/COLOR][/B]
**[COLOR=#000000][FONT=Arial][https://lh6.googleusercontent.com/MFC9QqiNAEj3ooH4epJDuEuDy6uSL6YyQ6ue7N8UVEU2C3Dj5AHf1aVcugUFMOubPsnwb55nEfGua8HrEITNKRM86hZvsiGIdQk1AZaoRNrvqa9wHyUzt4hBxYaKaWhjVJUw3PZQ](https://lh6.googleusercontent.com/MFC9QqiNAEj3ooH4epJDuEuDy6uSL6YyQ6ue7N8UVEU2C3Dj5AHf1aVcugUFMOubPsnwb55nEfGua8HrEITNKRM86hZvsiGIdQk1AZaoRNrvqa9wHyUzt4hBxYaKaWhjVJUw3PZQ)[/FONT][/COLOR]**

[COLOR=#222222][FONT=Verdana]I already sent an email to Xilinx and they told me that if the website mentions the Alveo cards are compatible with Ubuntu 18.04, then they should be compatible with any release of Ubuntu 18.04. Nonetheless they also added with reference to Vitis 2020.2 that even though 18.04.5 is probably ok, installing one of the releases that, according to the explicit mention of their website, are officially compatible with Vitis 2020.2, is recommended. [/FONT][/COLOR]

I already downloaded Ubuntu 18.04.4 and I also installed it successfully. Right after installing this release I disabled all automatic updates to make sure that no change got made to the release I installed, that means Ubuntu 18.04.4. But I experienced the problems I already mentioned on my first post of this thread and I still do not how to overcome them.

---


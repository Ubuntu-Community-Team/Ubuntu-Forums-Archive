---
title: "Lubuntu 10.10 sha256 checksum result"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by Hralgmir on 2011-03-23
[FONT=Times New Roman][SIZE=2]I have obtained the following result for a sha256 checksum for lubuntu 10.10.iso :[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]\31561c7ab4c0aaa48d2033e4629a20fe74c634e0098bf9ffa3906ef18d536f4b .[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Is this correct?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]I have been able to verify the MD5 sum which was [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]098254aeb0153b10bcfce948c43a0df6 . [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]I cannot find any mention of the sha256 sum on the internet, has anyone else performed this check for lubuntu 10.10.iso, and did you get the same result?[/SIZE][/FONT]

---

### Post by cavalier911 on 2011-03-23
MD5SUMS SHA1SUMS SHA256SUMS for every Ubuntu ISO here: 
[http://mirror.anl.gov/pub/ubuntu-iso](http://mirror.anl.gov/pub/ubuntu-iso)

I always use bittorent to download ubuntu ISO as it guarantees the checksum is good.

---

### Post by Hralgmir on 2011-03-24
[FONT=Times New Roman][SIZE=2]Thankyou for your suggestions, however this is Lubuntu 10.10 and not Ubuntu. There does not seem to be any inclusion of Lubuntu checksum results on this site at present. I found the MD5 sum on these webpages: 
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]http://iso.linuxquestions.org/lubuntu/lubuntu-10.10/ 

[http://translate.google.co.uk/translate?hl=en&sl=zh-CN&u=http://people.ubuntu.com/~gilir/md5sum.txt&ei=gYOLTbrXBo6xhAeJnICxDg&sa=X&oi=translate&ct=result&resnum=4&ved=0CDQQ7gEwAw&prev=/search%3Fq%3DLubuntu%2B10.10%2Bmd5%2Bchecksum%2B%2522098254aeb0153b10bcfce948c43a0df6%2522%26hl%3Den%26lr%3D%26prmd%3Divns]("http://translate.google.co.uk/translate?hl=en&sl=zh-CN&u=http://people.ubuntu.com/%7Egilir/md5sum.txt&ei=gYOLTbrXBo6xhAeJnICxDg&sa=X&oi=translate&ct=result&resnum=4&ved=0CDQQ7gEwAw&prev=/search%3Fq%3DLubuntu%2B10.10%2Bmd5%2Bchecksum%2B%2522098254aeb0153b10bcfce948c43a0df6%2522%26hl%3Den%26lr%3D%26prmd%3Divns")[/SIZE][/FONT]   [FONT=Times New Roman][SIZE=2]

[http://downloads.k0k0.de/index.php?dir=Netbooks%2FASUS%2FEeePC%2F901%2FImages%2F](http://downloads.k0k0.de/index.php?dir=Netbooks%2FASUS%2FEeePC%2F901%2FImages%2F)[/SIZE][/FONT]  [FONT=Times New Roman][SIZE=2]

Searching for the sha256 checksum result on google comes back with "no results found" so there does not seem to be this information published on a readily searchable part of the web, unless the result I have obtained is incorrect, but searching for sha256 Lubuntu 10.10 does not give the required information either.[/SIZE][/FONT] [FONT=Times New Roman][SIZE=2]

I obtained the sha256 result by following the instructions on this webpage:[/SIZE][/FONT] [FONT=Times New Roman][SIZE=2]

[http://www.labtestproject.com/using_windows/step_by_step_using_sha256sum_on_windows_xp.html](http://www.labtestproject.com/using_windows/step_by_step_using_sha256sum_on_windows_xp.html)[/SIZE][/FONT]  [FONT=Times New Roman][SIZE=2]

but as I am using Windows Vista not XP I could not drag and drop as described, and after downloading the sha256sum.exe file and saving it to my Downloads folder, I had to type C:\Users\Myaccountname>Downloads\sha256sum.exe C:Users\Myaccountname\Downloads\lubuntu-10.10.iso into the cmd.exe window to get the result: [/SIZE][/FONT] [FONT=Times New Roman][SIZE=2]

[/SIZE][/FONT]  [FONT=Times New Roman][SIZE=2]\31561c7ab4c0aaa48d2033e4629a20fe74c634e0098bf9ffa  3906ef18d536f4b *C:\\Users\\Myaccountname\\Downloads\\lubuntu-10.10.iso .

I had saved both files to Downloads and you would need to alter the file path accordingly for your account name if anyone was to try this in Vista for themselves. There are other tools for getting a sha256 sum result for both Windows and other operating systems available on the internet, it appears. There also seems to be other checksum variants, but these two were the ones mentioned on the Ubuntu website.
Presumably other people will be downloading Lubuntu 10.10 and performing this test, so if you do so and read this, please reply with your results.
[/SIZE][/FONT]

---


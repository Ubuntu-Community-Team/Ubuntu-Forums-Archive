---
title: "Duel Boot Not Letting me Chose Between 2 Ubuntu's on One External Hard Drive"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by wildblaze on 2010-11-03
I recently really wanted to dive into the Ubuntu operating system and learn about it but not give up Windows until I understood it. I also didn't want to take up presious resources to have it installed on my main hard drive or have a virtual machine going. So I decided I would install ubuntu on my 500GB external hardrive and I would partition it 200GB for 32Bit Ubuntu 10.10, 200Gb for 64But ubuntu 10.10, and 100GB for storage. The reason I put 32Bit and 64Bit both on was so that I could run Ubuntu on my home computer with 8GB of ram fully and use the 32Bit version for when I'm on other computers without 4GB or more GB of ram.
 
I was able to install everything correctly but have run into a problem, when I start up the computer and chose to boot from my external hard drive in boot options it just loads a Ubuntu and does not let me chose which one I want to use.
 
If anyone has any sugestions to give me a choice between the 2 Ubuntu's it would be a big help.
 
Thank you

---

### Post by oldfred on 2010-11-04
Do you have grub2 installed in the MBR of the external? Which Ubuntu is in the MBR. Boot that copy and run this:

```
sudo update-grub
```If not sure of what is where, you can run from either install or a liveCD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---


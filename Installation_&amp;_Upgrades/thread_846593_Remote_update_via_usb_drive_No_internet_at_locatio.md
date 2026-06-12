---
title: "Remote update via usb drive? No internet at location."
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by diafygi on 2008-07-01
Hey all,

My friend has a desktop running Hardy, but he lives out in the middle of nowhere without internet access. He's wants to update the installed packages on his computer, but he doesn't want to lug his desktop into town to do it. We've been discussing this for a while, but we haven't found a solution.

Ideally, he would be able to generate a list of the installed packages on his desktop (with version numbers) and save it to a USB drive. Then, he could drive to town and download any updated packages based on this list. He is welcome to use my Ubuntu machine to do the downloading.

We've thought about APTonCD, but that just grabs cached apt .deb files. It won't download those files based a list and check for newer versions. We can't just download all of them, since that would take up too much space. The only way I know to generate a list of installed packages is 'dpkg --get-selections', but that doesn't have version numbers.

Once the updated packages are downloaded, he can use APTonCD to create a repository for the updated packages. So when he goes back to the original computer, it can see the new versions and install them.

So I need your help! Is there any way you can save a snapshot of your package manager installed files to a USB drive, take it somewhere with internet, and download the appropriate updated packages?

I would suspect this would be a very useful method for remote places. In Cuba, for instance, people would pass around files on USB drives since communications and internet were so controlled. I would think USB drives would be a great way to transport updated packages to remote locations from a central point of internet access. Now, all I need to find is a way for the remote locations to save their current installed packages and a way to download updates based on that list.

---

### Post by Pumalite on 2008-07-01
You could try:
Synaptic Package Manager>File>Generate package download script

---

### Post by diafygi on 2008-07-01
> **Pumalite said:**
> You could try:
Synaptic Package Manager>File>Generate package download script

I tried that, but it just creates a script of the marked packages. If he can't get an updated repository list (since he doesn't have the internet), he doesn't know what packages to mark. I'm looking for a way to backup a list of all of the installed packages with version numbers, and a way to download updates based on that list.

---


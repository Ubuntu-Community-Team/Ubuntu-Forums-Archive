---
title: "How do you install Irrlicht on Code::Blocks?"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by kelvin.illa on 2009-11-27
So, I've already downloaded Irrlicht and put it under the '/opt folder as said [here]("http://www.irrlicht3d.org/wiki/index.php?n=Main.InstallingIrrlicht") in the Irrlicht installation tutorial.

In the project wizard though, using the Irrlicht template, I lead it to the '/opt/irrlicht' directory but it says: 
[I]
"The path you entered seems valid, but this wizard
can't locate the following Irrlicht's include file:
irrlicht.h in it."[/I]

But it's there; it just can't find it.

Was I wrong in following the above installation instructions (meaning, the one I used isn't right)? How do you solve this unfound 'irrlicht.h' issue with Code::Blocks? Or is there a more proper way of installation?

Thanks.

---

### Post by abdulahad100 on 2009-12-17
this will help you

[http://www.irrlicht3d.org/wiki/index.php?n=Main.SettingUpCodeBlocksOnLinux](http://www.irrlicht3d.org/wiki/index.php?n=Main.SettingUpCodeBlocksOnLinux)

---

### Post by faldore on 2010-07-18
I also had trouble creating a Code::Blocks Irrlicht project.

Here is how I fixed it:

```
sudo apt-get install codeblocks
sudo apt-get install libglu-dev 
sudo apt-get install libgl1-mesa-dev 
sudo apt-get install libirrlicht1.7 
sudo apt-get install libirrlicht-dev 
sudo apt-get install libirrlicht-doc 
sudo apt-get install libglib2.0-dev 
sudo apt-get install gcc 
sudo apt-get install cpp 
sudo apt-get install g++ 
sudo apt-get install gpp 
sudo apt-get install libXxf86vm-dev
```

Then open CodeBlocks, new project, Irrlicht, for irrlicht location enter "/usr", set project location, etc.
Once project is generated, change line 70 of main.cpp to dimension2d<u32> instead of dimension2d<s32>

Then build and run.  Now it should work, except it won't load Sydney yet because it can't find the files, you will need to set those files yourself. that is easy enough.

---

### Post by vivichrist on 2012-01-01
none of this works now. and I'm getting frustrated. I need a simple way of generating a project in code blocks so I can just do the tutorials. why do these things have to be so windows-centric? in ubuntu 11.10 irrlicht includes are in the /usr/include/irrlicht folder and libs are in the /usr/lib folder. all the other x and gl headers are in /usr/lib/x86_64-linux-gnu and /usr/include/x86_64-linux-gnu folders.

---

### Post by vivichrist on 2012-01-02
actually it was simple enough just to create a template in code::blocks : [ATTACH]210099[/ATTACH]
This should work with ubuntu 11.10 default Irrlicht packages. Just unzip extract the contents into 
(home/user folder) ~/.codeblocks/UserTemplates 
seems to work for the tutorial code I have tried so far.

---


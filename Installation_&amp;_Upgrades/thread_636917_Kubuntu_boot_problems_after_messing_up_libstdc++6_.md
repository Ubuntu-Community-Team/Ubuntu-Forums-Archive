---
title: "Kubuntu boot problems after messing up libstdc++6 library"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by Psychey on 2007-12-10
First of all, hello and thanks for a great forum! :)

Had to make a new post sometime, and I guess this is the time. The whole story started when I wanted to get Xilinx ISE software to work with Kubuntu. The setup complained about the fact that no libstdc++5 seemed to be present, the message was about as follows:

"libstdc++.so.5: cannot open shared object file: No such file or directory"

Since v6 of the same library was installed I figured why not just make a symbolic link for it? I made the symbolic link "sudo ln -s libstdc++6 libstdc++5" in the /usr/lib folder and hoped for the best. This proved to be a rather naive thing to do as the setup next started to complain about not finding the right versions of sertain objects in this file, something like:

<program name>  /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by <program name>) 
<program name>  /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by <program name>)

I'm sorry for not being able to be completely specific(the objectnames/versions is taken from memory), but I have no way to get into Kubuntu and reproduce the errors atm :p Okay, so the symbolic link didn't work. Then I did the most stupid thing ever. I went online and grabbed the latest version of the libstdc++5 package, thinking I might just need both to cover all the different object versions. Fair enough, package downloaded and extracted. Then I copied the libstdc++5 file into /usr/lib ... ... ...

... .. (lots of strange stuff happening on screen)...

...Xserver restarts and halts about midway giving no real explaination why. Okay, I figured lets just retrace my steps. I boot up into terminal and notice that any command requiring the libstdc++6 library is now malfunctioning. The errors are similar to the ones two paragraphs up.

Okay so I guess the symbolic link I had in /usr/lib sent the contents of my v5 library file into the v6 (and native OS one)? And since this gave an instant failure I guess more data could've been corrupted in the same go?

Question is, can i somehow replace the broken library with a fresh one without using the built in functions that depends on the c++ library - such as apt-get? Or does this qualify for a reinstall? ;)

Got to love the power Linux gives you to mess things up huh? :)

Thanks heaps for any responses.

---


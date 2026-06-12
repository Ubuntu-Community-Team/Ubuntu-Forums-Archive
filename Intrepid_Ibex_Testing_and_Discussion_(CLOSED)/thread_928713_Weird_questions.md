---
title: "Weird questions"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xlinuks on 2008-09-24
Hi,
I have a text file on a NTFS file system (or whatever other FS) called say "file.txt" and as I double click it from Ubuntu (Intrepid or other version) it asks me whether to open the text file or to execute it. Don't you think guys that this is silly and how make that this doesn't happen for normal users?

---

### Post by DrMega on 2008-09-24
> **xlinuks said:**
> Hi,
I have a text file on a NTFS file system (or whatever other FS) called say "file.txt" and as I double click it from Ubuntu (Intrepid or other version) it asks me whether to open the text file or to execute it. Don't you think guys that this is silly and how make that this doesn't happen for normal users?

The way Ubuntu handles double-clicking a file depends on its flags. If it's executable flag is set, then Ubuntu will offer to execute it. It seems to be an MS thing that we associate certain behaviour with certain file extensions. I used various systems before Windows was ever released and they used flags rather than extensions to decide how to handle a file, so it seems to be that it is Windows that's the odd one out, and not Ubuntu.

I'm not being anti-windows or pro-linux here, it just makes more sense to me that way. When you think about it, relying on a file extension to tell the system what to do with a file kind of makes flags redundant, whereas if you let the flags talk to the OS, then the extension is freed up for its original purpose of indicating to the user and various apps what the file is about.

file.txt in a Windows environment is often what you get when scandisk finds lost clusters and doesn't know what to do with them, so it doesn't make sense for an OS to assume that just because it has a .txt extension, that it is a human readable text file.

---

### Post by Quikee on 2008-09-24
Such a behavior is IMHO correct and makes sense even if the type of the file can be determined via and extension. For example if you have an executable bash script - what is your intent, to run it (via terminal or not) or to edit it when you double click.

---

### Post by xlinuks on 2008-09-24
Thanks, however Ubuntu luckily does not handle double-clicking depending on a file's flag (thank God), it only takes that into consideration.
As an example, I just set the executable flag on a .avi video file and the system doesn't even try execute the avi (it knows that it's a video file nonetheless, despite the executable flag), it launches another program to display the video in my case "kaffeine" - it would be ridiculous to ask the user whether he wants to execute video file(s).
I think the same applies to .txt files, the system should at least check whether it's capable of executing that/the file. You know, what exactly is it about to execute since (in my case) it contains plain text? Since the .txt extension is widely used across platforms I think it's worth improving Ubuntu in this regard as well.
Or put the execution flag on .jpg flags - the system doesn't try to execute them (as some kind of binaries).
For text files that are meant to be executed there's at least a #!/bin/sh or similar starting line.

---

### Post by xlinuks on 2008-09-24
I only mean it should not ask brain dead questions about executing a .txt file when there's text like "14:30 meeting at the University" - and Ubuntu asks "do you want to execute or display the file?", a normal user's reaction would be "wtf..".
Text files that are meant to be executed either have no extension or something like .py, .sh or alike along with (an optional) hint which program must execute the script. You should give in this is silly.. really.

---

### Post by phenest on 2008-09-24
It is quite possible to remove the extension from an existing file, and Ubuntu will still know what it is and how to handle it. Windows would have been in a complete mess if you did that.

---

### Post by xlinuks on 2008-09-24
Why does then Ubuntu not execute .avi files, pictures and other stuff?

---

### Post by dro0g on 2008-09-24
Look under Preferences -> Behavior in Nautilus. There's a setting for Executable Text Files:
 * Run executable text files when they are opened
 * View executable text files when they are opned
 * Ask each time

I think ask each time is the default.

---

### Post by DrMega on 2008-09-24
> **xlinuks said:**
> I only mean it should not ask brain dead questions about executing a .txt file when there's text like "14:30 meeting at the University" - and Ubuntu asks "do you want to execute or display the file?", a normal user's reaction would be "wtf..".
Text files that are meant to be executed either have no extension or something like .py, .sh or alike along with (an optional) hint which program must execute the script. You should give in this is silly.. really.

If the 'executable' flag is set and the file contains text, Ubuntu isn't going to attempt to work out whether or not that text is valid shell script or anything. Your "14:30 meeting at the University" text could just as easily of been some invalid script. Ubuntu isn't human, it can't judge just by looking and say "oh that's plain english, it's not for me to run", it recognises that it is text and that it could be a shell script.

---

### Post by xlinuks on 2008-09-24
All I mean is that the .txt extension deserves the attention to be checked before asked, just as in the other reasonable cases Ubuntu did. How many times have you met a .txt file meant for execution? I'm using Ubuntu for almost 2 years and have never had such a case and since, quite the opposite - the .txt files were _always_ meant to be read, not executed, isn't there something to think about usability?
dro0g - thanks, I know about that option, but it goes into the "either/or" applying to all text files regardless which isn't quite the usability I would like people to get.

PS: nautilus however does read the (first lines of the text) file and detect whether this is a bash, ruby or python script, so it still kinda figures out whether this is "plain english" or a known script and it's Nautilus who decides what to do, but even if this was not true my suggestion still applies.

---

### Post by Quikee on 2008-09-24
> **xlinuks said:**
> All I mean is that the .txt extension deserves the attention to be checked before asked, just as in the other reasonable cases Ubuntu did. How many times have you met a .txt file meant for execution? I'm using Ubuntu for almost 2 years and have never had such a case and since, quite the opposite - the .txt files were _always_ meant to be read, not executed, isn't there something to think about usability?

Forget about the extension - all nautilus cares about is that the user is trying to execute a file that is marked executable and he sees that it contains only text which might be a script - then he asks what to actually do. You don't want this - then why do you have a *.txt file marked as executable in the first place.

What it could be done is a little nicer message box - explaining the situation more precisely, make "un-mark execute" available or something like that.

> **xlinuks said:**
> PS: nautilus however does read the (first lines of the text) file and detect whether this is a bash, ruby or python script, so it still kinda figures out whether this is "plain english" or a known script and it's Nautilus who decides what to do, but even if this was not true my suggestion still applies.

And what if you have a script file in a language nautilus does not support? How should he distinguish then? Why make such wild guesses instead of asking?

---

### Post by xlinuks on 2008-09-24
For some reason the .txt files on the ntfs partition are marked as executable, I don't know why.
The PS explains another point, that nautilus does read the/some text from the text file and does analyse it, to what extent - to the one that its developers implemented.
The whole thread is somewhat hijacked, all I mean since Nautilus doesn't execute some files that do have the executable flag, why not add this extension to that list, for the reason I said earlier. Once again: how many times did anyone meet .txt files ment to be executed?

---

### Post by xlinuks on 2008-09-24
I'm saying this because of the overall "experience" one gets - not only is the default text editor "gedit" slow to startup, you might/are also being asked whether that is an executable. And since it (in my experience) never is - the casual windows user makes a parallel to the (blazing) experience he has opening text files in windows and makes conclusions. I mean it's not only Microsoft's illegal actions that Linux is alegedly on under 1% of desktops, it's also our fault for using bigotry instead of usability decisions.

---

### Post by ronacc on 2008-09-24
a .txt file could be (and sometimes is ) a script, hence the executeable flag . It is logical for ubuntu to ask if you wish to execute the file or display it when you click on the file in nautilus ( you might wish to edit it rather than run it) as mentioned above you can chose the behavior that pleases you in preferences . Side note ! on the Amiga there were 8 use flags RWEDHASP read ,write,execute,delete,hidden,archive,sctipt and pure.

---

### Post by Quikee on 2008-09-25
> **xlinuks said:**
> For some reason the .txt files on the ntfs partition are marked as executable, I don't know why.

Maybe this is the problem then - not the executable text file. 

> **xlinuks said:**
> The PS explains another point, that nautilus does read the/some text from the text file and does analyse it, to what extent - to the one that its developers implemented.
The whole thread is somewhat hijacked, all I mean since Nautilus doesn't execute some files that do have the executable flag, why not add this extension to that list, for the reason I said earlier. Once again: how many times did anyone meet .txt files ment to be executed?

I think you don't understand. Nautilus doesn't care if about the extension when executing. When he examines the content he sees that it is a text file (he sees that it is a "text/plain" via MIME - upon which he decides how to execute) and assumes it might be a script as it is marked as an EXECUTABLE! Theoretically you can have a script file that it "text/plain" because you could use a language with extension not known to nautilus also who says that a extension-less python file may not be executed as it is detected as a "text/plain" - after all it is marked as EXECUTABLE.

Deciding that a *.txt file should have a special treatment in such a case is just a wild guess and nonsense. But if you want you can do this - probably by editing "/etc/mime.types" and deciding that a *.txt file is not text/plain anymore but some type that fits your behavior.

> **xlinuks said:**
> I'm saying this because of the overall "experience" one gets - not only is the default text editor "gedit" slow to startup, you might/are also being asked whether that is an executable. And since it (in my experience) never is - the casual windows user makes a parallel to the (blazing) experience he has opening text files in windows and makes conclusions. I mean it's not only Microsoft's illegal actions that Linux is alegedly on under 1% of desktops, it's also our fault for using bigotry instead of usability decisions.

The question (message box) is valid - it is something fishy with the file and the user should be cautious and decide what to do (just to not execute the file by mistake).

If you don't agree with this behavior you should file a bug and not argue with us that think this is the correct behavior - argue this with the nautilus developers itself.

---

### Post by jfbilodeau on 2008-09-25
What about giving some intelligence to Nautilus:

Check the first two chars of the file.
If it's "#!", prompt user (maybe with a friendlier dialog)
Else display content.

Another suggestion may be to display the content of the file be default, and add an 'Execute' on the context (right-click) menu.

---


---
title: "Intrepid sucks (3 months to boot!)"
date: 2008-08-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-08-17
I have previously run both gutsy and hardy as alpha tests on my main machine with minimal disruption and have always been impressed with the stability of something so complex at such an early stage of development. I had every intention of doing the same with intrepid, installed as soon as I was able and all was fine for a few week until I decided to do a re-install from scratch. Since that day I have been utterly unable to get this beast to install/boot/anything.

Today I decided that alpha 4 is the live cd for me, this is the intrepid that will show me I don't need a degree in rocket science to operate my 3g modem. However on both my HiGrade va250d and HP tx1000x laptops the boot menu loads, I select the first option to live boot and it hangs. The system has not crashed, caps lock light responds and ejecting the cd results in a reboot prompt being displayed but left to it's own devices it just sits at the boot menu perpetually.

So, I have to ask the question, is anyone good enough to actually get this thing going? Does anyone know what the problem is?

---

### Post by napsy on 2008-08-17
I don't know what's your problem. Intrepid is alpha quality software and you should know the system probably is unstable/broken/buggy and alpha software can't be compared to previous alpha versions. The best way is to make a bug report for your problem.

---

### Post by bobbocanfly on 2008-08-17
> **macroshaft said:**
> I have previously run both gutsy and hardy as alpha tests on my main machine with minimal disruption and have always been impressed with the stability of something so complex at such an early stage of development. I had every intention of doing the same with intrepid, installed as soon as I was able and all was fine for a few week until I decided to do a re-install from scratch. Since that day I have been utterly unable to get this beast to install/boot/anything.

Today I decided that alpha 4 is the live cd for me, this is the intrepid that will show me I don't need a degree in rocket science to operate my 3g modem. However on both my HiGrade va250d and HP tx1000x laptops the boot menu loads, I select the first option to live boot and it hangs. The system has not crashed, caps lock light responds and ejecting the cd results in a reboot prompt being displayed but left to it's own devices it just sits at the boot menu perpetually.

So, I have to ask the question, is anyone good enough to actually get this thing going? Does anyone know what the problem is?

Filing a bug is highly likely to get you a response from a developer, though I would try with a different ISO burn and then if that doesnt work, the latest daily. If none of these methods work, then please file a bug.

---

### Post by macroshaft on 2008-08-17
I don't have a problem, I just feel that intrepid is far more unstable than the last few versions. Whether that is due to largr changes under the surface or because I'm not on laptops rather than desktops I don't know.

I wanted to leave a post here before filling a bug because I wanted to know if anyone has experienced it or if a bug is already filed. However I have heard mention of a daily build but have no idea how to get it.

Other than these hiccups I'm looking forward to intrepid becoming another quality product as always.

---

### Post by alastair on 2008-08-17
> **macroshaft said:**
> I select the first option to live boot and it hangs. The system has not crashed, caps lock light responds and ejecting the cd results in a reboot prompt being displayed but left to it's own devices it just sits at the boot menu perpetually.

Kernels change with every release and some may cause issues. Even on release, some kernels may need extra options.

Edit the boot options to see where we hang :.

F6 on first option
Remove "splash" and "quiet" options - to see boot logs

Boot (enter)

You might see where the hang happens ...

You could also try the above but add kernel args e.g.

F6 on first option
Remove "splash" and "quiet" options - to see boot logs
At end add "acpi=off" (after the "--" chars)
Boot ...

The "acpi=off" is an example only - but I have to use it to boot my system. I don't like it, but there you are.

Log a bug - and include machine/hardware detail.

Alastair

---

### Post by ronacc on 2008-08-17
there have been problems with the livecd from the start , if you want to do an install try the alternate install cd . As a note though the alpha4 livecd works ok on my desktop and yes for me it is more buggy than fiesty ,gutsy or hardy though not as bad as edgy which was never useable for me even the release .

---

### Post by mike1234 on 2008-08-17
I upgraded my 8.04 to 8.10 last night. "Alt+F2" update-manager -d  "New Distribution Update". So far it is working great. I did the same with 8.04 from 7.
I've found this a safer way of trying new Operating systems. Clean installs are just asking for trouble. Besides, you knew the risks involved. My upgrade went just fine with only older kernels and related 8.04 system files being deleted. Compiz, Nvidia settings, etc. still here and working. When I upgraded to 8.04 my sound was broke until final release. I've beta tested software clear back to Windows 95. I like the Adventure!

M.

---

### Post by Nullack on 2008-08-17
I like the adventure too!

Sometimes I get frustrated at the 7000+ views of every poor souls opinion about the new theme and I see people come onto this section of the forum and whinge about their particular bug asking for help. That to me isnt real contributions to the Alpha. I think we need to encourage people to yes, fix their problems, but also to fix whats wrong in Intrepid as a whole working within the existing defect process.

So here with this one the bloke hasnt been able to use Intrepid Alphas for 3 months. Well, where's the 3 months work of bug work? What contribution has been made to report them? Too many people say "this doesnt work" and then vanish without actually contributing to the *Alpha* process.

Anyway the stability of any Alpha really isnt a factor within Canonicals control - its chiefly driven by the changes coming from key upstream projects like the kernel, X, gnome etcetc.

---

### Post by macroshaft on 2008-08-17
Nullack, it may surprise you to learn that there are many of us who wish to contribute but have this strange double life in which half is devoted to working to pay bills. Not everyone has the time to work on debugging all the time. I have seen many people on here complaining about how people test ubuntu but NEVER has anyone given any practical and straightforward guidance on what is being done wrong.

Firstly you should be proud that we have a system where someone who is knowledgeable and capable of doing the debugging can work alongside the likes of me, who is still getting a feel for this. Secondly I was under the impression that discussing a potential bug on here was an important step towards identifying and reporting it. The ability to ask for help in these early stages (and don't say that I shouldn't be testing in the early stages because no matter how experienced you are you will still be a beginner in testing one day) and obtain guidance on how testing is done is very important.

Now, please tell me, my live cd refuses to boot, there are no error messages. Without referring to posts in this thread and without just quoting an answer to me, tell me what process do I go through to identify and then file the bug?

---

### Post by ronacc on 2008-08-17
what steps have ou taken to try to get it to boot ? have you tried that alastair posted above ? when it hangs try alt+F1 and see if a terminal comes up , it may give you a little information there . simply wont boot doesnt give us much to work with .

---

### Post by Nullack on 2008-08-17
Here is some information on reporting bugs:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Simply, once something happens that wasnt what you expected, lets call that an "issue". I welcome anyone and will help them out who genuinely wants to improve Ubuntu's quality to the best I can. Many others here do the same. Im not going to help people though who arent committed to genuinely doing their part with bugs which in the case of a new person learning Ubuntu is not time consuming at all. Especially given the Alpha status, genuinely doing your part is important - users on Alphas cant realistically have the save demands as users on producion releases.

Honestly, it wont take more than a few minutes to do most basic bug reports. If you dont know all the details something is better than nothing and you can always add to it later as time allows.

So you can use this forum, IRC, ubuntu wiki, google etcetc to see if your issue is actually a bug or is something else like an idea. In your case I think its clear its a bug because youve got a failure to boot. So now we know were pretty sure its a bug I would try to come up with as much info as possible within your time constraints.

To help narrow down the issue can I please suggest:

1. checksum the cd to determine its ok
2. Carefully observe the point at which it fails and let us know that. This is important for example as if the kernel is booting but X is failing we can do things to diagnose it further. As Alastair said even if it is the kernel theres still boot options that can be put to it. The kernel team has alot of info on reporting kernel bugs we can use as guidance.

---

### Post by macroshaft on 2008-08-17
Not yet, but now I've been given a thread to pull on I'll give it a go as soon as the laptop is free to do so.

---

### Post by Slug71 on 2008-08-17
Dude i understand your frustration. I installed Intrepid trying to overcome problems i had with Hardy and also ran into a lot of issues with Intrepid after a week or so but you have to realize that this is still a Alpha release. There will still be 2 more Alphas before the Beta and the Final.

---


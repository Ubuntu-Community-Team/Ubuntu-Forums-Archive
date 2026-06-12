---
title: "Ubuntu patch management tool"
date: 2022-02-26
forum: Installation &amp; Upgrades
---

### Post by sameerpatel37 on 2022-02-26
I want to patch multiple ubuntu servers. Please provide name of the best open source linux patch management tool with no license (Free of cost).

---

### Post by TheFu on 2022-02-26
I use ssh and apt-get. This is basic Unix and has been how thousands and thousands of systems at sites around the world have been managed for 30+ yrs.  

bash, ssh, {package manager}.

Find a 20 yr old UNIX Power Tools book (probably $0.50 at any used book store) and *Beginning Bash Scripting Guide* [https://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](https://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)

In Unix/Linux, we don't often need to buy anything, since simple scripts can do the work using built-in tools.

I have been a UNIX/Linux admin over 25 yrs. I cannot think of **any** time we paid for administrative tools over all that time. I've spent $100+ millions on hardware and $200+million on software for applications, but not administration.

Basically, if you pay for pretty GUIs, your boss will like the meaningless graphs, but it won't actually do more than what the built-in tools accomplish, since the built-in tools will still be used under the covers.

Linux isn't Windows.  Never forget that.

---

### Post by him610 on 2022-02-26
> UNIX Power Tools book 
Seeing TheFu refer to this book struck a chord with me. Several years ago I came into possession of *The Unix CD Bookshelf* by O'Reilly that included Unix Power Tools along with five other Unix related books. O'Reilly also published *The Linux Web Server CD Bookshelf* and *The Perl CD Bookshelf.* I have copies of all three that I  transfer from computers-to-be-retired to their newer replacements. Useful references to this day.

---

### Post by TheFu on 2022-02-26
> **him610 said:**
> Seeing TheFu refer to this book struck a chord with me. Several years ago I came into possession of *The Unix CD Bookshelf* by O'Reilly that included Unix Power Tools along with five other Unix related books. O'Reilly also published *The Linux Web Server CD Bookshelf* and *The Perl CD Bookshelf.* I have copies of all three that I  transfer from computers-to-be-retired to their newer replacements. Useful references to this day.

I own all those CD-Bookshelves (hopefully they fixed the terrible java-server interface since my versions) and I own probably 8 of the O'Reilly books separately from those. 

Excellent references, though for Perl I can recommend just 3 books are needed these days.  My favorite, by far is _Mastering Perl_.  I met the author, Brian Foy, for dinner a few years ago when he was in town. Great guy.  The chapter on creating commented regex is freakin' amazing. It changed, completely, how I write regex in perl so each part gets a separate comment.  Regex isn't write-once code anymore, but highly maintainable now.  About 8 other chapters have stuck with me too. Excellent advanced perl5 resource, but it isn't for beginners.

The 2nd is by Chromatic - [https://pragprog.com/titles/swperl/modern-perl-fourth-edition/](https://pragprog.com/titles/swperl/modern-perl-fourth-edition/) This is a free ebook available in many different formats. I find it a great intermediate text.  

For Learning Perl ... Start with Randal's [https://www.oreilly.com/library/view/learning-perl-6th/9781449311063/](https://www.oreilly.com/library/view/learning-perl-6th/9781449311063/) coauthored by Brian and Tom.

I'm a perl guy.  Today, not many people are. They choose to follow the masses to Python, which is a fine language too.  I just don't like the mandate indentation styles. I'm old and set in my ways for how indentation should be. Only Python forces anyone to go against their own style. Every other language let's a programmer decide which style is most readable.

UNIX Power Tools is sorta a survey of all the different CLI tools in /usr/bin/ that have been part of UNIX for 45+ yrs. If you've only seen a hammer all your life, you'd never know that screwdrivers exist. Walking into a professional's wood shop and seeing all sorts of odd tools that we haven't any clue the purpose for each ...   That's what I mean by "survey" - learn about 20+ different tools and the types of problems they each can solve.  I think each tool has a 'cookbook' solution, which can be used for all the most common needs.

---


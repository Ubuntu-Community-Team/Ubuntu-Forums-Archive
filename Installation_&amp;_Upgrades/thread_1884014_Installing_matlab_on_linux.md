---
title: "Installing matlab on linux"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by shad0w7 on 2011-11-20
Is it possible to do it using wine? I already tried it but I get many errors. Any tutorial online ? Or anybody has a solution?
I am using ubuntu 64-bit 11.10

---

### Post by MG&amp;TL on 2011-11-20
It's available for linux as-is ( If I'm thinking of the right matlab):

[http://www.mathworks.co.uk/products/matlab/requirements.html]("http://www.mathworks.co.uk/products/matlab/requirements.html")

---

### Post by qleak on 2011-11-20
matlab has a native linux version

[http://www.mathworks.com/help/techdoc/matlab_env/bs6j5lz.html#f8-29076](http://www.mathworks.com/help/techdoc/matlab_env/bs6j5lz.html#f8-29076)

---

### Post by 3Miro on 2011-11-20
You should get the Linux version of Matlab, even if you can get the windows version working with wine (which I doubt), you will not find much help since people use the Linux version under Linux.

---

### Post by MG&amp;TL on 2011-11-20
I imagine if you can prove that you bought the windows version, they'll be happy to let you.


Is matlab any good? My little brother wants it for christmas....<sigh>

---

### Post by 3Miro on 2011-11-20
> **MG&TL said:**
> I imagine if you can prove that you bought the windows version, they'll be happy to let you.


Is matlab any good? My little brother wants it for christmas....<sigh>

Matlab is basically the industry standard for Numerical Analysis and Engineering. How little is your little brother, MATLAB is College level stuff and only as a Graduate Student would one be expected to really tap into its power.

---

### Post by boast on 2011-11-20
> **MG&TL said:**
> 
Is matlab any good? My little brother wants it for christmas....<sigh>

if you're a researcher, its what you'd be staring at all day.

---

### Post by MG&amp;TL on 2011-11-20
> **3Miro said:**
> Matlab is basically the industry standard for Numerical Analysis and Engineering. How little is your little brother, MATLAB is College level stuff and only as a Graduate Student would one be expected to really tap into its power.

He's 12, but he's autistic and does university level maths.

---

### Post by 3Miro on 2011-11-20
> **MG&TL said:**
> He's 12, but he's autistic and does university level maths.

If he does University Math indeed, then Matlab would be good for him. The other option is Mathematica, which is more for symbolic work and it is more theoretical. Matlab is for numerical and applied math, oriented towards Engineering applications.

---

### Post by MG&amp;TL on 2011-11-20
> **3Miro said:**
> If he does University Math indeed, then Matlab would be good for him. The other option is Mathematica, which is more for symbolic work and it is more theoretical. Matlab is for numerical and applied math, oriented towards Engineering applications.

He into things like fluid dynamics, so I guess a modelling library/engineering is good?

---

### Post by pjd99 on 2011-11-20
GNU Octave is an open source numerical analysis tool with near-identical syntax to Matlab. This would serve as a good introduction to the Matlab environment and scripting language, and exists in the Ubuntu repositories. There are plenty of add-on packages that provide identical or similar functionality to Matlab "Toolboxes", though the GUI builders for filters/controllers etc don't exist.

Worth a look before shelling out for Matlab.

---

### Post by MG&amp;TL on 2011-11-20
Thanks, I'll give that a look.

---

### Post by rewyllys on 2011-11-20
> **3Miro said:**
> If he does University Math indeed, then Matlab would be good for him. The other option is Mathematica, which is more for symbolic work and it is more theoretical. Matlab is for numerical and applied math, oriented towards Engineering applications.
I have no desire to denigrate MatLab, which is indeed powerful.  

But IMHO it would be fairer to characterize Mathematica as being able not only to handle the kinds of engineering applications that MatLab handles, but also as handling numerous other fields, including probability and statistics, image processing, number theory, etc.  Of course, Mathematica is even more expensive than MatLab (although academic discounts are available to qualified persons).

BTW, I second the recommendation of GNU Octave as handling most everything that MatLab handles.

---

### Post by 3Miro on 2011-11-21
> **rewyllys said:**
> I have no desire to denigrate MatLab, which is indeed powerful.  

But IMHO it would be fairer to characterize Mathematica as being able not only to handle the kinds of engineering applications that MatLab handles, but also as handling numerous other fields, including probability and statistics, image processing, number theory, etc.  Of course, Mathematica is even more expensive than MatLab (although academic discounts are available to qualified persons).

That is not a fair statement. Matlab can also do statistics and number theory and any symbolic computations. The difference between Matlab and Mathematica is how they handle the Symbolic vs Numeric computations. Mathematica is very powerful when it comes to symbolic computations or number theory, however, it is at best clumsy if you have to do numerical linear algebra. Matlab is the exact opposite, numerical stuff comes naturally, the symbolic stuff was added as an after-thought. 

> 
BTW, I second the recommendation of GNU Octave as handling most everything that MatLab handles.

My Ph.D. dissertation was on fluid dynamics. Everybody that I know in this field uses Matlab (or Fortan or C/C++). While Octave is a good starting point, it cannot do all the Matlab code. Thus if you download some fluid dynamics software off the Internet, then Octave may not be sufficient.

If one isn't an actual researcher, then it is safe to start with Octave to see how far they can go. After all it doesn't cost anything to try out Octave.

---

### Post by rewyllys on 2011-11-21
> **3Miro said:**
> . . . . Mathematica is very powerful when it comes to symbolic computations or number theory, however, it is at best clumsy if you have to do numerical linear algebra. . . .
I readily agree with this comment, having--like almost all mathematicians--been trained to prefer visualizing vectors as columns, not rows.

My dissertation antedated Matlab and Mathematica; in those bad old days, I had to write my programs in FORTRAN.:cry:

---

### Post by 3Miro on 2011-11-21
> **rewyllys said:**
> 
My dissertation antedated Matlab and Mathematica; in those bad old days, I had to write my programs in FORTRAN.:cry:

Actually when it comes to the hardest problems in fluids, neither Matlab nor Mathematica can handle the work-load. At this point everything is moving to FORTRAN or C/C++. Only one part of my dissertation was about Matlab, the heavy computations were carried out in C++. I view Matlab as a tool to test the algorithms before I spend the time to do the real implementation in C/C++.

---


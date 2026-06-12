---
title: "Im a ubuntu noobie."
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Ubunaab on 2011-01-21
Helllo i am new
And i really have problems with installing
I do it with terminal but it never works.
how?

---

### Post by oldos2er on 2011-01-21
Installing what exactly? If you can copy the terminal output of your command and the system's response, it would help.

---

### Post by Ubunaab on 2011-01-22
nevermind, however what does this error means?

> 
linuxexe: /usr/include/boost/thread/pthread/condition_variable_fwd.hpp:38: boost::condition_variable::~condition_variable(): Assertion `!pthread_cond_destroy(&cond)' failed.
Aborted


and this?

[IMG]http://img04.imgland.net/kAQI3IOaUG.png[/IMG]

---

### Post by davidmohammed on 2011-01-22
what application are you running?

How did you install it i.e. from software center?  Download from the web? - if so where did you download it and what instructions did you to compile and install?

---

### Post by Ubunaab on 2011-01-22
I am connected from my windows 7 to a dedicated server > ubuntu and i tried to run a application to put my online game online.

---

### Post by davidmohammed on 2011-01-22
We need more help from you on what you are trying to do.

Please post some web-links of the application you are trying to run?

Please visit the ubuntu-forums - absolute beginners forum and click on the last two stickies.  They give you instructions on what information we need you to post to help us help you.

---

### Post by Ubunaab on 2011-01-22
1.
[http://otland.net/f18/8-54-forgotten-server-0-3-6pl1-crying-damson-59924/](http://otland.net/f18/8-54-forgotten-server-0-3-6pl1-crying-damson-59924/)

2. 
Possible to run on ubuntu if compiling what my friend did

3.
we got enough space and such things.

---

### Post by Ubunaab on 2011-01-25
help!

---

### Post by realzippy on 2011-01-25
The link you gave in post #7 is useless since you have to become a registered user to watch the content.

---

### Post by Ubunaab on 2011-01-25
[http://otland.net/f18/opentibia-dll-files-v1-4b-1042/](http://otland.net/f18/opentibia-dll-files-v1-4b-1042/)

[http://otland.net/subversion.php?svn=public&file=listing.php&repname=forgottenserver&path=%2Ftags%2F0.3.6pl1%2F#afc4b6d12c172c363c6e8951ec3c5c164]("http://otland.net/subversion.php?svn=public&file=listing.php&repname=forgottenserver&path=%2Ftags%2F0.3.6pl1%2F#afc4b6d12c172c363c6e8951ec3c5c164")

[http://otland.net/project.php?projectid=2](http://otland.net/project.php?projectid=2)

[http://otland.net/blogs/the-forgotten-server/](http://otland.net/blogs/the-forgotten-server/)

[http://www.speedyshare.com/633718469.html](http://www.speedyshare.com/633718469.html)

;)


> #ifndef BOOST_THREAD_PTHREAD_CONDITION_VARIABLE_FWD_HPP
#define BOOST_THREAD_PTHREAD_CONDITION_VARIABLE_FWD_HPP
// Distributed under the Boost Software License, Version 1.0. (See
// accompanying file LICENSE_1_0.txt or copy at
// [http://www.boost.org/LICENSE_1_0.txt](http://www.boost.org/LICENSE_1_0.txt))
// (C) Copyright 2007-8 Anthony Williams

#include <boost/assert.hpp>
#include <pthread.h>
#include <boost/thread/mutex.hpp>
#include <boost/thread/locks.hpp>
#include <boost/thread/thread_time.hpp>
#include <boost/thread/xtime.hpp>

#include <boost/config/abi_prefix.hpp>

namespace boost
{
    class condition_variable
    {
    private:
        pthread_cond_t cond;
        
        condition_variable(condition_variable&);
        condition_variable& operator=(condition_variable&);

    public:
        condition_variable()
        {
            int const res=pthread_cond_init(&cond,NULL);
            if(res)
            {
                throw thread_resource_error();
            }
        }
        ~condition_variable()
        {
            BOOST_VERIFY(!pthread_cond_destroy(&cond));
        }

        void wait(unique_lock<mutex>& m);

        template<typename predicate_type>
        void wait(unique_lock<mutex>& m,predicate_type pred)
        {
            while(!pred()) wait(m);
        }

        bool timed_wait(unique_lock<mutex>& m,boost::system_time const& wait_until);
        bool timed_wait(unique_lock<mutex>& m,xtime const& wait_until)
        {
            return timed_wait(m,system_time(wait_until));
        }

        template<typename duration_type>
        bool timed_wait(unique_lock<mutex>& m,duration_type const& wait_duration)
        {
            return timed_wait(m,get_system_time()+wait_duration);
        }

        template<typename predicate_type>
        bool timed_wait(unique_lock<mutex>& m,boost::system_time const& wait_until,predicate_type pred)
        {
            while (!pred())
            {
                if(!timed_wait(m, wait_until))
                    return pred();
            }
            return true;
        }

        template<typename predicate_type>
        bool timed_wait(unique_lock<mutex>& m,xtime const& wait_until,predicate_type pred)
        {
            return timed_wait(m,system_time(wait_until),pred);
        }

        template<typename duration_type,typename predicate_type>
        bool timed_wait(unique_lock<mutex>& m,duration_type const& wait_duration,predicate_type pred)
        {
            return timed_wait(m,get_system_time()+wait_duration,pred);
        }

        typedef pthread_cond_t* native_handle_type;
        native_handle_type native_handle()
        {
            return &cond;
        }

        void notify_one();
        void notify_all();
    };
}

#include <boost/config/abi_suffix.hpp>

#endif



> 
theforgottenserver: /usr/include/boost/thread/pthread/condition_variable_fwd.hpp:38: boost::condition_variable::~condition_variable(): Assertion `!pthread_cond_destroy(&cond)' failed.
Aborted


---

### Post by realzippy on 2011-01-25
?

---

### Post by davidmohammed on 2011-01-25
ubuntu noobie,

   visualise this - you cant see the person and you cant speak to them but you can pass them one piece of paper... you have to describe in words what your issue is - what you are using, what you are attempting, how you have done something, what you are seeing.

At the moment you havent actually done any of that!

Let us try and help you - please reread the beginners forum stickies and look the examples for the detail we need to help you.

---

### Post by Ubunaab on 2011-01-25
that is not possible
because you need to get what a tibia OT server is!

But it is hard to do that because i got a problem but i dont get that ubuntu terminal sh*t

---

### Post by realzippy on 2011-01-26
Hm,googling "set up tibia OT server" gives a bunch of howtos...

eg:
[http://tibiahelp.com/articles_29_OT-Server-WhichHow-and-why.html](http://tibiahelp.com/articles_29_OT-Server-WhichHow-and-why.html)

Can't you try this and tell us were your problem is?
And tell us which OS/Ubuntu version you use?

---


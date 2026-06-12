---
title: "Compile c++ program after installation of opencascade"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by silversoldier on 2012-01-26
Hi,

I have Ubuntu 11.10 on a 32-bit computer with 2GB memory, 512MB nVidia video card and 500GB HD. I installed the following opencascade module with sudo apt-get install <package_name>.
ibopencascade-dev: OpenCASCADE CAE platform library development files
libopencascade-foundation-6.5.0: OpenCASCADE CAE platform shared library
 libopencascade-foundation-dev: OpenCASCADE CAE platform library development files
libopencascade-modeling-6.5.0: OpenCASCADE CAE platform shared library
libopencascade-modeling-dev: OpenCASCADE CAE platform library development files
libopencascade-ocaf-6.5.0: OpenCASCADE CAE platform shared library
libopencascade-ocaf-dev: OpenCASCADE CAE platform library development files
libopencascade-ocaf-lite-6.5.0: OpenCASCADE CAE platform shared library
libopencascade-ocaf-lite-dev: OpenCASCADE CAE platform library development files
libopencascade-visualization-6.5.0: OpenCASCADE CAE platform shared library
libopencascade-visualization-dev: OpenCASCADE CAE platform library development files
opencascade-draw: OpenCASCADE CAE platform shared library
opencascade-examples: OpenCASCADE CAE platform library input examples

I added /usr/include/opencascade in GNU c++'s include path. However, I was not able to find where the *.so of opencascade is. When compiling the short program below, "IGESControl_Reader" can not be resolved. Please advise what are the paths for c++ link or the environment that I need. Thanks.

#include <iostream>
#include <IGESData_IGESModel.hxx>
#include <IGESData_IGESEntity.hxx>

int main()
{
    using namespace std;
    cout << "Test c++ with opencascade.";
    
    IGESControl_Reader aReader;
    return 0;
}

BR, Silversoldier

---


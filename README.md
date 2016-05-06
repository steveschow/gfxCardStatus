# gfxCardStatus.i

This is a fork from Cody Krieger's gfxCardStatus project: https://github.com/codykrieger/gfxCardStatus

The purpose of this project is to introduce a few changes that improve the way gfxCardStatus handles Integrated-Only mode.  This is of particular interest to MacBookPro users that have the dreaded kernel panic problem from the nVidia GPU.  

Currently gfxCardStatus v2.3 is unable to maintain Integrated-Only mode because OSX will sometimes force the machine back to Discrete mode when exiting certain apps.  Unfortunately OSX is not aware that gfxCardStatus has set the "ONLY" flag (rather then dynamic switching), and so the system state will be changed to Discrete-Only, which is not usually desirable.

This version of gfxCardStatus will contain code changes that make it possible to maintain Integrated GPU as much as possible.  Unfortunately it will not be possible to have 100% Integrated Usage because OSX does force to Discrete mode when exiting certain apps, which cannot be prevented.  However, this version of gfxCardStatus will minimize the amount of time that the Discrete GPU is used by switching back to Integrated mode as soon as possible.   And it will avoid getting trapped in Discrete-Only mode by the logical error explained above.

The initial idea for this project was created by an older fork by highandfew (https://github.com/highandfew/gfxCardStatus) some years ago that has not been pulled into the main project, nor has it been maintained ever since.  This project will initially have highandfew's change integrated with the more recent code from gfxCardStatus, but will also provide a few more benefits, which shall be outlined here as they are completed.  

An effort will be made to keep this project up to date with the main gfxCardStatus project it has been forked from, with regards to other bug fixes and enhancements which may come forth in the future.

## Binary Releases
Binary releases of this fork can probably be found here: https://github.com/steveschow/gfxCardStatus/releases

## Building from source

Please see build instructions from: https://github.com/codykrieger/gfxCardStatus
Note, the project currently has some build issues which I will try to correct here in this fork.  If you have trouble building, then follow this workaround: 
  - open the subproject called <code>Pods</code> in Xcode, and build it, it builds some libraries
  - copy the libraries into the LIB path of the parent gfxCardStatus project
  - build gfxCardStatus in Xcode

I hope to have this problem corrected in this fork and hopefully can get pulled into the main project too, and I also hope to have binaries released on this repo, so stay tuned.


## License

Licensed under the New BSD License.

Copyright (c) 2010-2012, Cody Krieger and other contributors
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:  
    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.  
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in the
      documentation and/or other materials provided with the distribution.  
    * Neither the name of gfxCardStatus nor the
      names of its contributors may be used to endorse or promote products
      derived from this software without specific prior written permission.  

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL CODY KRIEGER BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

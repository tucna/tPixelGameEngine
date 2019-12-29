# tPixelGameEngine
Simple engine based on **Javidx9**'s `oclPixelGameEngine` - https://github.com/OneLoneCoder/olcPixelGameEngine

The biggest difference in comparisson with the original is *DirectX 11* based rendering instead of *OpenGL*. Because of that it is necessary to distribute shader binaries together with the engine file.

# Usage
Usage is the same as for the original version. You should add the header file from `engine` folder to your project and also you **must put there two shader files `vs.cso` and `ps.cso`**. After that you should write a new class, derive from `tDX::PixelGameEngine` and that is basically it. Check a code:

```cpp
#define T_PGE_APPLICATION
#include "tPixelGameEngine.h"

class Example : public tDX::PixelGameEngine
{
public:
  Example()
  {
    sAppName = "Example";
  }

public:
  bool OnUserCreate() override
  {
    // Called once at the start, so create things here
    return true;
  }

  bool OnUserUpdate(float fElapsedTime) override
  {
    // called once per frame
    for (int x = 0; x < ScreenWidth(); x++)
      for (int y = 0; y < ScreenHeight(); y++)
        Draw(x, y, tDX::Pixel(rand() % 255, rand() % 255, rand() % 255));

    DrawString(5, 5, "TUCNA");

    return true;
  }
};


int main()
{
  Example demo;
  if (demo.Construct(250, 250, 4, 4))
    demo.Start();

  return 0;
}

```

In your class overload `OnUserUpdate` method, in `main` create object, call `Construct` and `Start` in the end. That's all.

You can read original documentation [here](https://github.com/OneLoneCoder/olcPixelGameEngine/wiki).

# Screenshot
<p align="center">  
  <img src="doc/s1.png">
</p>

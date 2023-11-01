# Pan
这里是一个实现从多个文件名最后三个字母为.sgn的二进制文件读取字节,转换为C语言形式的char数组,并写入txt文件的示例:

```csharp
using System;
using System.IO;
using System.Text;

namespace BinaryToCharArray
{
    class Program
    {
        static void Main(string[] args)
        {
            string[] files = Directory.GetFiles(@"filePath", "*.sgn");

            StringBuilder output = new StringBuilder();

            foreach (string file in files)
            {
                if (IsSgnFile(file))
                {
                    char[] chars = ReadFileToCharArray(file);

                    string charArray = ToCArrayString(chars);

                    output.AppendLine(charArray);
                }
            }

            File.WriteAllText("output.txt", output.ToString());
        }

        static bool IsSgnFile(string filename) 
        {
            return filename.EndsWith(".sgn", StringComparison.OrdinalIgnoreCase);
        }

        static char[] ReadFileToCharArray(string filename)
        {
            // 读取文件字节
            // 转换为char数组

            return chars; 
        }

        static string ToCArrayString(char[] chars)
        {
            return "char[" + chars.Length + "] = {" + 
               string.Join(",", chars.Select(c => $"0x{((int)c).ToString("X")}")) + "};";
        }
    }
}
```

主要步骤:

1. 获取多个.sgn文件
2. 读取转换为char数组
3. 构建C数组字符串格式
4. 收集所有文件内容
5. 输出到txt文件

这样可以方便其他语言引用生成的内容。

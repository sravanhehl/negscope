# negscope

**拆解提示词里的否定句，区分「禁止做」与「不必做」。**

`negscope` —— 识别否定词作用域，判断是硬禁止、软建议还是不必要求，给出可执行性判定

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`negscope.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install sravanhehl-negscope
```

装完直接用命令名调用：

```bash
negscope --help
```

也可以不用安装，直接把 `negscope.py` 拷走用——它只依赖标准库。

## 为什么需要它

把否定句按作用域切开，逐词判断强度，而不是看到否定词就当禁止

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 提示词否定句语义 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python negscope.py --file input.txt
python negscope.py --text "示例内容"
python negscope.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 切分按行与标点做，不理解语义段落。
- 空槽判定靠槽位关键词，措辞特殊时会漏。

## 跑测试

```bash
python test_negscope.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/sravanhehl/negscope>

---

## 关于作者

sravanhehl 做提示词否定句语义相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://sravanhehl.github.io>
- 仓库：<https://github.com/sravanhehl/negscope>

## 许可

MIT，见 [LICENSE](LICENSE)。

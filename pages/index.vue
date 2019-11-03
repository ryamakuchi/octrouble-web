<template>
  <div>
    <el-header>Octrouble Web</el-header>
    <el-container>
      <el-main>
        <p>
          GitHub リポジトリを検索して Issues を見ることができます。
        </p>

        <el-input
          v-model="input"
          placeholder="rails/rails"
          class="input-with-select"
        >
          <el-button slot="append" icon="el-icon-search"></el-button>
        </el-input>

        <div class="card-list">
          <el-card v-for="card in cardList" :key="card.index" class="box-card">
            <div slot="header">
              <span> user/repo{{ card.title }} </span>

              <el-button
                type="danger"
                icon="el-icon-delete"
                circle
                @click="deleteCard(card.index)"
              ></el-button>
            </div>
            <div
              v-for="issues in card.issues"
              :key="issues.index"
              class="text item"
            >
              <el-button type="text" @click="open(issues)">
                Issue title
                {{ issues.title }}
              </el-button>
            </div>
          </el-card>
        </div>
      </el-main>
    </el-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: '',
      cardList: [
        {
          title: 'user/repo1',
          issues: [
            {
              title: 'issue title 1',
              description: 'Lorem ipsum dolor sit amet'
            },
            {
              title: 'issue title 2',
              description: 'Lorem ipsum dolor sit amet'
            }
          ]
        },
        {
          title: 'user/repo2',
          issues: [
            {
              title: 'issue title 1',
              description: 'Lorem ipsum dolor sit amet'
            },
            {
              title: 'issue title 2',
              description: 'Lorem ipsum dolor sit amet'
            }
          ]
        },
        {
          title: 'user/repo3',
          issues: [
            {
              title: 'issue title 1',
              description: 'Lorem ipsum dolor sit amet'
            },
            {
              title: 'issue title 2',
              description: 'Lorem ipsum dolor sit amet'
            }
          ]
        },
        {
          title: 'user/repo4',
          issues: [
            {
              title: 'issue title 1',
              description: 'Lorem ipsum dolor sit amet'
            },
            {
              title: 'issue title 2',
              description: 'Lorem ipsum dolor sit amet'
            }
          ]
        }
      ]
    }
  },
  methods: {
    open(issues) {
      this.$alert(issues.description, issues.title)
    },
    deleteCard(index) {
      this.cardList.splice(index, 1)
    }
  }
}
</script>

<style lang="scss" scoped>
p {
  color: #24292e;
}
.el-container {
  background-color: #eeeeee;
  min-height: calc(100vh - 60px);
  padding: 0 10% 10%;

  @media screen and (max-width: 768px) {
    padding: 0 5% 10%;
  }
}

.el-header {
  background-color: #24292e;
  color: #eeeeee;
  text-align: center;
  line-height: 60px;
}

.el-main {
  color: #24292e;
  text-align: center;
}

.el-input-group {
  width: 80%;
  margin: 20px auto 0;

  @media screen and (max-width: 768px) {
    width: 100%;
  }
}

.el-input__inner {
  background-color: #fefefe;
}

.card-list {
  margin: 20px auto 0;
  display: flex;
  text-align: left;
  justify-content: flex-start;
  flex-wrap: wrap;

  .el-card {
    width: calc(50% - 40px);
    margin: 20px;

    &__header div {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-weight: bold;
    }

    @media screen and (max-width: 768px) {
      width: calc(100%);
      margin: 10px 0;
    }
  }

  .item {
    border-bottom: 1px solid #ebeef5;

    &:last-child {
      border-bottom: none;
    }
  }
}
</style>
